.PHONY: all icons
APP=FreeBracketsTKD

all: icons
	nativefier http://localhost/brackets \
		--icons icons/$(APP).icns \
		--show-menu-bar \
		--name $(APP)

icons:
	mkdir -p icons/$(APP).iconset
	for i in 16 32 64 128 256 512; do \
		sips -s format png icons/src/icon.png -s dpiHeight 72.0 -s dpiWidth 72.0 -Z $$i --out icons/$(APP).iconset/icon_$$i\x$$i.png; \
	done; \
	for i in 16 32 64 128 256 512; do \
		((j=$$i * 2)); \
		sips -s format png icons/src/icon.png -s dpiHeight 72.0 -s dpiWidth 72.0 -Z $$j --out icons/$(APP).iconset/icon_$$i\x$$i\@2x.png; \
	done; \
	iconutil -c icns icons/$(APP).iconset

clean:
	rm -Rf icons/$(APP).iconset
	rm -Rf icons/$(APP).icns
	rm -Rf $(APP)-darwin-x64
