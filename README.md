# AI for Oncology QuPath extension catalog

A [catalog](https://qupath.readthedocs.io/en/latest/docs/intro/extensions.html) of
[QuPath](https://qupath.github.io) extensions maintained by the AI for Oncology group (NKI-AI).

## Adding this catalog in QuPath

1. Open QuPath (0.6 or newer).
2. Go to `Extensions` -> `Manage extensions`.
3. Click `Manage extension catalogs` -> `Add`.
4. Enter this repository URL:

   ```
   https://github.com/NKI-AI/qupath-extension-catalog
   ```

5. Install an extension by clicking the `+` next to it. QuPath will keep it up to
   date as new releases are added here.

## Extensions

| Extension | Description | Source |
| --- | --- | --- |
| QuPath FastSlide extension | Read whole-slide images via FastSlide | [NKI-AI/qupath-extension-fastslide](https://github.com/NKI-AI/qupath-extension-fastslide) |

## Updating the catalog

Edit [`catalog.json`](catalog.json) and add a new entry to the relevant extension's
`releases` array, pointing `main_url` at the JAR asset of a published GitHub
Release. The asset URL must resolve exactly (filename included). Then commit and
push:

```bash
git add catalog.json
git commit -m "Add qupath-extension-fastslide vX.Y.Z"
git push
```

The `validate-catalog` GitHub Action validates `catalog.json` against the
[`extension-catalog-model`](https://github.com/qupath/extension-catalog-model)
schema on every push and pull request.

### Validate locally

```bash
python3 -m venv env && . env/bin/activate
pip install git+https://github.com/qupath/extension-catalog-model
python -c "from extension_catalog_model.model import Catalog; Catalog.model_validate_json(open('catalog.json').read()); print('valid')"
```
