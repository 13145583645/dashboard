MODULES_DIRECTORY := $(shell dirname $(realpath $(firstword $(MAKEFILE_LIST))))
API_DIRECTORY = $(MODULES_DIRECTORY)/api
METRICS_SCRAPER_DIRECTORY = $(MODULES_DIRECTORY)/metrics-scraper
WEB_DIRECTORY = $(MODULES_DIRECTORY)/web
MODULES := $(API_DIRECTORY) $(WEB_DIRECTORY) $(METRICS_SCRAPER_DIRECTORY)

MAKEFLAGS += -j2

.PHONY: --run $(MODULES)
--run: $(MODULES)

$(MODULES):
	@$(MAKE) --directory=$@ $(TARGET)
