XBUILD=/Applications/Xcode.app/Contents/Developer/usr/bin/xcodebuild
PROJECT_ROOT=.
PROJECT=$(PROJECT_ROOT)/XALAlertBanner.xcodeproj
TARGET=XALAlertBanner

all: libALAlertBannerSDK.a

libXALAlertBanner-i386.a:
	$(XBUILD) -project $(PROJECT) -target $(TARGET) -sdk iphonesimulator -configuration Release clean build
	-mv $(PROJECT_ROOT)/build/Release-iphonesimulator/lib$(TARGET).a $@

libXALAlertBanner-armv7.a:
	$(XBUILD) -project $(PROJECT) -target $(TARGET) -sdk iphoneos -arch armv7 -configuration Release clean build
	-mv $(PROJECT_ROOT)/build/Release-iphoneos/lib$(TARGET).a $@

libALAlertBannerSDK.a: libXALAlertBanner-i386.a libXALAlertBanner-armv7.a
	lipo -create -output $@ $^

clean:
	-rm -f *.a *.dll
