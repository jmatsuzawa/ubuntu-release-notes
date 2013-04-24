MASTER_DOC_URL = https://wiki.ubuntu.com/RaringRingtail/ReleaseNotes/Lubuntu?action=raw
MASTER_DOC = release-notes.txt
LOCALIZED_DOC = release-notes-ja.txt 
POTFILE = release-notes.pot
POFILE = ja.po

THRESHOLD = 0
EXTFLAGS =
PO4AFLAGS += --keep $(THRESHOLD) $(EXTFLAGS)

.PHONY: all translate
all: translate
translate: $(LOCALIZED_DOC)
$(LOCALIZED_DOC): $(POFILE)
	po4a-translate $(PO4AFLAGS) --format text --master $(MASTER_DOC) --po $(POFILE) --localized $@

.PHONY: clean
clean:
	if test -e $(LOCALIZED_DOC); then rm $(LOCALIZED_DOC); fi

.PHONY: update-po
update-po: $(MASTER_DOC)
	po4a-updatepo --format text --master $(MASTER_DOC) --po $(POFILE) --previous --msgmerge-opt='--no-wrap --no-location' 

.PHONY: pot
pot: master-doc
	po4a-gettextize --format text --master $(MASTER_DOC) --po $(POTFILE)

.PHONY: master-doc
$(MASTER_DOC): master-doc
master-doc:
	w3m "$(MASTER_DOC_URL)" > $(MASTER_DOC)

