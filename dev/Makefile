SHELL := /bin/bash -o pipefail

ifndef VERBOSE
.SILENT:
endif

.DEFAULT_GOAL := all
.PHONY: backup restore resetAdminPW precheck configure secret dbready dbcheck precompile waiteln all

sleep:
	echo "Sleeping ..."
	sleep infinity

zero backup restore resetAdminPW precheck configure secret dbready dbcheck precompile permissions waiteln dev:
	echo -e "\x1B[38;2;255;255;255mRunning task: [$@]\x1B[0m"
	[[ -f /embed/lib/env      ]] && source /embed/lib/env && \
	[[ -f /embed/lib/utils.sh ]] && source /embed/lib/utils.sh && \
	[[ -f "./scripts/$@.sh"   ]] && \
	TASKNAME="$@" ./bin/timeit bash "./scripts/$@.sh"
	echo -e "\x1B[90mTask [$@] finished.\x1B[0m"

all-eln: precheck configure secret dbready dbcheck precompile permissions
all-worker: permissions waiteln
all-dev: zero precheck configure secret dbready dbcheck precompile permissions dev
