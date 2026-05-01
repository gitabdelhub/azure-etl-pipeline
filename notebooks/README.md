# Notebooks

## Execution Order

Run the notebooks in the following order against your Databricks cluster:

1. **Ingestion (Bronze)** — handled by the Azure Data Factory pipeline (no notebook; ADF copies the raw CSV to the `bronze` ADLS container).
2. **`Prime_Silver_Layer_Transformation.ipynb`** — reads from Bronze, cleans and standardises the data, writes a Delta table to the `silver` container.
3. **`gold_layer_transfo.ipynb`** — reads from Silver, enriches the data (date parsing, category splits), writes the final Delta table to `gold_layer.prime_gold`.

## Required Configuration

Before running the notebooks, make sure the following are in place:

| Parameter | Where to set |
|---|---|
| Azure Storage account name | Update `storage_account_name` in each notebook if different from `adlsprimeabdel` |
| ADLS access key | Store in Azure Key Vault and expose via a Databricks secret scope named `kv-scope` with key `adls-key` |
| ADLS containers | Create `bronze`, `silver`, and `gold` containers in your ADLS Gen2 account |

### Setting up Databricks Secrets

```bash
databricks secrets create-scope --scope kv-scope --scope-backend-type AZURE_KEYVAULT \
  --resource-id <key-vault-resource-id> --dns-name <key-vault-dns-name>
```

Then reference the key in notebooks with:

```python
storage_account_key = dbutils.secrets.get(scope="kv-scope", key="adls-key")
```
