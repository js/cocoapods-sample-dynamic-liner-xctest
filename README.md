A sample project for a Cocoapods related linker issue

contains:
- A fresh "single view" project created with Xcode 10.1 (10B61) on Mojave 10.14.1 (18B75)
- Added a pod for the test target

Builds fine, but errors at runtime when running the tests with:

```
2018-11-30 09:34:04.387892+0100 Podtest3[48059:1672289] Failed to load test bundle from file:///Users/johan/Library/Developer/Xcode/DerivedData/Podtest3-gxhjknkxpvtkjfcnjwaactlgrgig/Build/Products/Debug-iphonesimulator/Podtest3.app/PlugIns/Podtest3Tests.xctest/: Error Domain=NSCocoaErrorDomain Code=3587 "dlopen_preflight(/Users/johan/Library/Developer/Xcode/DerivedData/Podtest3-gxhjknkxpvtkjfcnjwaactlgrgig/Build/Products/Debug-iphonesimulator/Podtest3.app/PlugIns/Podtest3Tests.xctest/Podtest3Tests): Library not loaded: @rpath/libswiftSwiftOnoneSupport.dylib
  Referenced from: /Users/johan/Library/Developer/Xcode/DerivedData/Podtest3-gxhjknkxpvtkjfcnjwaactlgrgig/Build/Products/Debug-iphonesimulator/Podtest3.app/PlugIns/Podtest3Tests.xctest/Frameworks/Nimble.framework/Nimble
  Reason: image not found" UserInfo={NSLocalizedFailureReason=The bundle is damaged or missing necessary resources., NSLocalizedRecoverySuggestion=Try reinstalling the bundle., NSFilePath=/Users/johan/Library/Developer/Xcode/DerivedData/Podtest3-gxhjknkxpvtkjfcnjwaactlgrgig/Build/Products/Debug-iphonesimulator/Podtest3.app/PlugIns/Podtest3Tests.xctest/Podtest3Tests, NSDebugDescription=dlopen_preflight(/Users/johan/Library/Developer/Xcode/DerivedData/Podtest3-gxhjknkxpvtkjfcnjwaactlgrgig/Build/Products/Debug-iphonesimulator/Podtest3.app/PlugIns/Podtest3Tests.xctest/Podtest3Tests): Library not loaded: @rpath/libswiftSwiftOnoneSupport.dylib
  Referenced from: /Users/johan/Library/Developer/Xcode/DerivedData/Podtest3-gxhjknkxpvtkjfcnjwaactlgrgig/Build/Products/Debug-iphonesimulator/Podtest3.app/PlugIns/Podtest3Tests.xctest/Frameworks/Nimble.framework/Nimble
  Reason: image not found, NSBundlePath=/Users/johan/Library/Developer/Xcode/DerivedData/Podtest3-gxhjknkxpvtkjfcnjwaactlgrgig/Build/Products/Debug-iphonesimulator/Podtest3.app/PlugIns/Podtest3Tests.xctest, NSLocalizedDescription=The bundle “Podtest3Tests” couldn’t be loaded because it is damaged or missing necessary resources.}
2018-11-30 09:34:04.388562+0100 Podtest3[48059:1672289] libXCTestBundleInject Arguments:
2018-11-30 09:34:04.628628+0100 Podtest3[48059:1672289]   /Users/johan/Library/Developer/CoreSimulator/Devices/3F81AC72-B2DA-4398-838A-3C858C018293/data/Containers/Bundle/Application/5DC80776-8C35-4EB5-A0FA-3AB4EAAA2E11/Podtest3.app/Podtest3
2018-11-30 09:34:04.628724+0100 Podtest3[48059:1672289]   -NSTreatUnknownArgumentsAsOpen
2018-11-30 09:34:04.628813+0100 Podtest3[48059:1672289]   NO
2018-11-30 09:34:04.628906+0100 Podtest3[48059:1672289]   -ApplePersistenceIgnoreState
2018-11-30 09:34:04.628990+0100 Podtest3[48059:1672289]   YES
2018-11-30 09:34:04.629093+0100 Podtest3[48059:1672289] libXCTestBundleInject Environment:
2018-11-30 09:34:04.629293+0100 Podtest3[48059:1672289]   CFFIXED_USER_HOME = /Users/johan/Library/Developer/CoreSimulator/Devices/3F81AC72-B2DA-4398-838A-3C858C018293/data/Containers/Data/Application/2ECB613E-A056-44EA-B47B-508A4C212C63
2018-11-30 09:34:04.629423+0100 Podtest3[48059:1672289]   OS_ACTIVITY_DT_MODE = YES
2018-11-30 09:34:04.629518+0100 Podtest3[48059:1672289]   SIMULATOR_RUNTIME_VERSION = 12.1
2018-11-30 09:34:04.629616+0100 Podtest3[48059:1672289]   SIMULATOR_AUDIO_DEVICES_PLIST_PATH = /Users/johan/Library/Developer/CoreSimulator/Devices/3F81AC72-B2DA-4398-838A-3C858C018293/data/var/run/com.apple.coresimulator.audio.plist
2018-11-30 09:34:04.629712+0100 Podtest3[48059:1672289]   __XPC_DYLD_FRAMEWORK_PATH = /Users/johan/Library/Developer/Xcode/DerivedData/Podtest3-gxhjknkxpvtkjfcnjwaactlgrgig/Build/Products/Debug-iphonesimulator
2018-11-30 09:34:04.629798+0100 Podtest3[48059:1672289]   CUPS_SERVER = /private/tmp/com.apple.launchd.uFZVczeiEh/Listeners
2018-11-30 09:34:04.629865+0100 Podtest3[48059:1672289]   SIMULATOR_VERSION_INFO = CoreSimulator 581.2 - Device: iPhone XR - Runtime: iOS 12.1 (16B91) - DeviceType: iPhone Xʀ
2018-11-30 09:34:04.630030+0100 Podtest3[48059:1672289]   DYLD_FALLBACK_LIBRARY_PATH = /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/Library/CoreSimulator/Profiles/Runtimes/iOS.simruntime/Contents/Resources/RuntimeRoot/usr/lib
2018-11-30 09:34:04.630104+0100 Podtest3[48059:1672289]   DYLD_FALLBACK_FRAMEWORK_PATH = /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/Library/CoreSimulator/Profiles/Runtimes/iOS.simruntime/Contents/Resources/RuntimeRoot/System/Library/Frameworks
2018-11-30 09:34:04.630253+0100 Podtest3[48059:1672289]   SIMULATOR_DEVICE_NAME = iPhone XR
2018-11-30 09:34:04.630385+0100 Podtest3[48059:1672289]   __XCODE_BUILT_PRODUCTS_DIR_PATHS = /Users/johan/Library/Developer/Xcode/DerivedData/Podtest3-gxhjknkxpvtkjfcnjwaactlgrgig/Build/Products/Debug-iphonesimulator
2018-11-30 09:34:04.630519+0100 Podtest3[48059:1672289]   IPHONE_TVOUT_EXTENDED_PROPERTIES = /Users/johan/Library/Developer/CoreSimulator/Devices/3F81AC72-B2DA-4398-838A-3C858C018293/data/Library/Application Support/Simulator/extended_display.plist
2018-11-30 09:34:04.630773+0100 Podtest3[48059:1672289]   DYLD_ROOT_PATH = /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/Library/CoreSimulator/Profiles/Runtimes/iOS.simruntime/Contents/Resources/RuntimeRoot
2018-11-30 09:34:04.630944+0100 Podtest3[48059:1672289]   SIMULATOR_BOOT_TIME = 1543563646
2018-11-30 09:34:04.631150+0100 Podtest3[48059:1672289]   XCTestConfigurationFilePath = /Users/johan/Library/Developer/Xcode/DerivedData/Podtest3-gxhjknkxpvtkjfcnjwaactlgrgig/Logs/Test/Test-Podtest3-2018.11.30_09-33-46-+0100.xcresult/1_Test/Diagnostics/Podtest3Tests-E893019A-F0EB-49A1-8BF7-8E953EF0556E/Podtest3Tests-94A975F9-27B8-4D76-B062-9A6AE3146A7F/LaunchSessions/24645537-2562-4A0B-9114-575D8A0A3D87/remote-container/tmp/Podtest3Tests-24645537-2562-4A0B-9114-575D8A0A3D87.xctestconfiguration
2018-11-30 09:34:04.631291+0100 Podtest3[48059:1672289]   SIMULATOR_EXTENDED_DISPLAY_PROPERTIES = /Users/johan/Library/Developer/CoreSimulator/Devices/3F81AC72-B2DA-4398-838A-3C858C018293/data/Library/Application Support/Simulator/extended_display.plist
2018-11-30 09:34:04.631508+0100 Podtest3[48059:1672289]   SIMULATOR_RUNTIME_BUILD_VERSION = 16B91
2018-11-30 09:34:04.631642+0100 Podtest3[48059:1672289]   SIMULATOR_MAINSCREEN_SCALE = 2.000000
2018-11-30 09:34:04.631762+0100 Podtest3[48059:1672289]   SIMULATOR_PRODUCT_CLASS = N841
2018-11-30 09:34:04.631963+0100 Podtest3[48059:1672289]   HOME = /Users/johan/Library/Developer/CoreSimulator/Devices/3F81AC72-B2DA-4398-838A-3C858C018293/data/Containers/Data/Application/2ECB613E-A056-44EA-B47B-508A4C212C63
2018-11-30 09:34:04.632079+0100 Podtest3[48059:1672289]   CA_ASSERT_MAIN_THREAD_TRANSACTIONS = 0
2018-11-30 09:34:04.632208+0100 Podtest3[48059:1672289]   NSUnbufferedIO = YES
2018-11-30 09:34:04.632397+0100 Podtest3[48059:1672289]   SIMULATOR_LEGACY_ASSET_SUFFIX = iphone
2018-11-30 09:34:04.632548+0100 Podtest3[48059:1672289]   TESTMANAGERD_SIM_SOCK = /private/tmp/com.apple.launchd.iOq30dOlPY/com.apple.testmanagerd.unix-domain.socket
2018-11-30 09:34:04.632692+0100 Podtest3[48059:1672289]   SIMULATOR_MEMORY_WARNINGS = /Users/johan/Library/Developer/CoreSimulator/Devices/3F81AC72-B2DA-4398-838A-3C858C018293/data/var/run/memory_warning_simulation
2018-11-30 09:34:04.652534+0100 Podtest3[48059:1672289]   SIMULATOR_MAINSCREEN_PITCH = 326.000000
2018-11-30 09:34:04.652645+0100 Podtest3[48059:1672289]   XPC_SERVICE_NAME = UIKitApplication:com.johansorensen.Podtest3[0x26e0][33927]
2018-11-30 09:34:04.652743+0100 Podtest3[48059:1672289]   SIMULATOR_MAINSCREEN_HEIGHT = 1792
2018-11-30 09:34:04.652815+0100 Podtest3[48059:1672289]   TMPDIR = /Users/johan/Library/Developer/CoreSimulator/Devices/3F81AC72-B2DA-4398-838A-3C858C018293/data/Containers/Data/Application/2ECB613E-A056-44EA-B47B-508A4C212C63/tmp
2018-11-30 09:34:04.652892+0100 Podtest3[48059:1672289]   SIMULATOR_LOG_ROOT = /Users/johan/Library/Logs/CoreSimulator/3F81AC72-B2DA-4398-838A-3C858C018293
2018-11-30 09:34:04.652987+0100 Podtest3[48059:1672289]   PATH = /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/Library/CoreSimulator/Profiles/Runtimes/iOS.simruntime/Contents/Resources/RuntimeRoot/usr/bin:/Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/Library/CoreSimulator/Profiles/Runtimes/iOS.simruntime/Contents/Resources/RuntimeRoot/bin:/Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/Library/CoreSimulator/Profiles/Runtimes/iOS.simruntime/Contents/Resources/RuntimeRoot/usr/sbin:/Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/Library/CoreSimulator/Profiles/Runtimes/iOS.simruntime/Contents/Resources/RuntimeRoot/sbin:/Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/Library/CoreSimulator/Profiles/Runtimes/iOS.simruntime/Contents/Resources/RuntimeRoot/usr/local/bin
2018-11-30 09:34:04.653339+0100 Podtest3[48059:1672289]   SIMULATOR_HID_SYSTEM_MANAGER = /Library/Developer/PrivateFrameworks/CoreSimulator.framework/Resources/Platforms/iphoneos/Library/Frameworks/SimulatorHID.framework
2018-11-30 09:34:04.653420+0100 Podtest3[48059:1672289]   SIMULATOR_MAINSCREEN_WIDTH = 828
2018-11-30 09:34:04.653513+0100 Podtest3[48059:1672289]   IOS_SIMULATOR_SYSLOG_SOCKET = /tmp/com.apple.CoreSimulator.SimDevice.3F81AC72-B2DA-4398-838A-3C858C018293/syslogsock
2018-11-30 09:34:04.653591+0100 Podtest3[48059:1672289]   SIMULATOR_CAPABILITIES = /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/Library/CoreSimulator/Profiles/DeviceTypes/iPhone Xʀ.simdevicetype/Contents/Resources/capabilities.plist
2018-11-30 09:34:04.653664+0100 Podtest3[48059:1672289]   RWI_LISTEN_SOCKET = /private/tmp/com.apple.launchd.02g9rM8zB2/com.apple.webinspectord_sim.socket
2018-11-30 09:34:04.653744+0100 Podtest3[48059:1672289]   XPC_SIMULATOR_LAUNCHD_NAME = com.apple.CoreSimulator.SimDevice.3F81AC72-B2DA-4398-838A-3C858C018293
2018-11-30 09:34:04.653815+0100 Podtest3[48059:1672289]   CA_DEBUG_TRANSACTIONS = 0
2018-11-30 09:34:04.653906+0100 Podtest3[48059:1672289]   SIMULATOR_ROOT = /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/Library/CoreSimulator/Profiles/Runtimes/iOS.simruntime/Contents/Resources/RuntimeRoot
2018-11-30 09:34:04.654091+0100 Podtest3[48059:1672289]   XCInjectBundleInto = /Users/johan/Library/Developer/Xcode/DerivedData/Podtest3-gxhjknkxpvtkjfcnjwaactlgrgig/Build/Products/Debug-iphonesimulator/Podtest3.app/Podtest3
2018-11-30 09:34:04.654280+0100 Podtest3[48059:1672289]   DYLD_LIBRARY_PATH = /Users/johan/Library/Developer/Xcode/DerivedData/Podtest3-gxhjknkxpvtkjfcnjwaactlgrgig/Build/Products/Debug-iphonesimulator
2018-11-30 09:34:04.654436+0100 Podtest3[48059:1672289]   XPC_FLAGS = 0x0
2018-11-30 09:34:04.654641+0100 Podtest3[48059:1672289]   DYLD_INSERT_LIBRARIES = /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/Library/CoreSimulator/Profiles/Runtimes/iOS.simruntime/Contents/Resources/RuntimeRoot/usr/lib/libMainThreadChecker.dylib
2018-11-30 09:34:04.654821+0100 Podtest3[48059:1672289]   MTC_CRASH_ON_REPORT = 1
2018-11-30 09:34:04.655011+0100 Podtest3[48059:1672289]   SIMULATOR_HOST_HOME = /Users/johan
2018-11-30 09:34:04.655179+0100 Podtest3[48059:1672289]   DYLD_FRAMEWORK_PATH = /Users/johan/Library/Developer/Xcode/DerivedData/Podtest3-gxhjknkxpvtkjfcnjwaactlgrgig/Build/Products/Debug-iphonesimulator:
2018-11-30 09:34:04.655354+0100 Podtest3[48059:1672289]   SIMULATOR_AUDIO_SETTINGS_PATH = /Users/johan/Library/Developer/CoreSimulator/Devices/3F81AC72-B2DA-4398-838A-3C858C018293/data/var/run/simulatoraudio/audiosettings.plist
2018-11-30 09:34:04.655538+0100 Podtest3[48059:1672289]   SIMULATOR_SHARED_RESOURCES_DIRECTORY = /Users/johan/Library/Developer/CoreSimulator/Devices/3F81AC72-B2DA-4398-838A-3C858C018293/data
2018-11-30 09:34:04.655718+0100 Podtest3[48059:1672289]   SQLITE_ENABLE_THREAD_ASSERTIONS = 1
2018-11-30 09:34:04.655881+0100 Podtest3[48059:1672289]   SIMULATOR_UDID = 3F81AC72-B2DA-4398-838A-3C858C018293
2018-11-30 09:34:04.656059+0100 Podtest3[48059:1672289]   SIMULATOR_MODEL_IDENTIFIER = iPhone11,8
2018-11-30 09:34:04.656234+0100 Podtest3[48059:1672289]   IPHONE_SIMULATOR_ROOT = /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/Library/CoreSimulator/Profiles/Runtimes/iOS.simruntime/Contents/Resources/RuntimeRoot
2018-11-30 09:34:04.656425+0100 Podtest3[48059:1672289]   __XPC_DYLD_LIBRARY_PATH = /Users/johan/Library/Developer/Xcode/DerivedData/Podtest3-gxhjknkxpvtkjfcnjwaactlgrgig/Build/Products/Debug-iphonesimulator
2018-11-30 09:34:04.656581+0100 Podtest3[48059:1672289]   CLASSIC = 0
2018-11-30 09:34:04.656768+0100 Podtest3[48059:1672289]   IPHONE_SHARED_RESOURCES_DIRECTORY = /Users/johan/Library/Developer/CoreSimulator/Devices/3F81AC72-B2DA-4398-838A-3C858C018293/data

````