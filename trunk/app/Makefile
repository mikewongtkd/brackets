.PHONY: all icons
APP=FreeBracketsTKD
OS=darwin-x64

all: icons app

app:
	nativefier http://localhost/brackets \
		--icon icons/$(APP).icns \
		--show-menu-bar \
		--maximize \
		--name $(APP)
	./bin/change-url $(APP) $(OS)
	cp -Rf ../frontend/html/include ../frontend/html/index.html $(APP)-$(OS)/$(APP).app/Contents/Resources/app

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

clean: clean-icons clean-app

clean-icons:
	rm -Rf icons/$(APP).iconset
	rm -Rf icons/$(APP).icns

clean-app:
	rm -Rf $(APP)-darwin-x64
