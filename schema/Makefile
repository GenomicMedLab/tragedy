.PHONY: defs FORCE
.SECONDARY:
.SUFFIXES:
.DELETE_ON_ERROR:

JSYAMLS:=vrs.yaml
JSONS:=${JSYAMLS:.yaml=.json}

all: tragedy.json defs

tragedy.json: tragedy-js.yaml
	jsy2js.py <$< >$@

tragedy-js.yaml: tragedy.yaml
	source2jsy.py <$< >$@

defs:
	rm -rf defs
	y2t.py tragedy.yaml

## # npm install -g json-dereference-cli
## %.json: %.yaml
## 	json-dereference -s $< -o $@


watch:
	-while true; do ls -1 *.yaml | entr -dn make ${JSONS}; done
