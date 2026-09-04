# FEDDA Hub module pack

A folder FEDDA reads in addition to its own workflows. Point `pack_paths` in
`app/config/runtime_settings.json` at it, or run the installer that does that.

    modules.json        the card, and which tabs it owns
    workflow_api.json   one entry per tab, in the same shape as the app's own
    workflows/          the graphs those entries name
    models.json         where each model comes from

Every file is optional. A pack that only adds a model source is `models.json`
and nothing else.

## Adding a workflow

1. Convert the ComfyUI export with the app's `scripts/ui_to_api.py`
2. Save it under `workflows/<family>/<name>.json`
3. Add an entry to `workflow_api.json` whose `filename` is that relative path
4. Add the tab id to the module's `tabs` in `modules.json`
5. Add any model it needs to `models.json`, or it will be red on every machine
   but the one it was built on

The app always wins a name collision: a pack adds, it never replaces.
