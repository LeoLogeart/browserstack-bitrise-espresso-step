# BrowserStack App Automate - Espresso

[![Step changelog](https://shields.io/github/v/release/bitrise-steplib/steps-virtual-device-testing-for-android?include_prereleases&label=changelog&color=blueviolet)](https://github.com/browserstack/browserstack-bitrise-espresso-step/releases)

# @rishabhe to update the link

Run Espresso tests on BrowserStack

<details>
<summary>Description</summary>

Run your Espresso tests on BrowserStack App Automate. This step collects the built APK from `$BITRISE_APK_PATH` and test apk from `$BITRISE_TEST_APK_PATH` environment variables.

## Configure the Step

Before configuring this step, make sure you install [Bitrise CLI](https://github.com/bitrise-io/bitrise) on your machine.

Complete the following steps:

1. Open the Workflow you want to use in the Workflow Editor.
​
2. Before adding this step, add the [Android Build for UI testing](https://www.bitrise.io/integrations/steps/android-build-for-ui-testing) Step to your Workflow & configure it.
​
4. Add the **BrowserStack App Automate - Espresso** step right after the **Android Build for UI testing** step.
​
5. Add your BrowserStack Username and Access Key in the **Authentication** step input.
​
6. For **App & Test Suite** step inputs, the **Android Build for UI Testing** step exports an APK and a test APK, and their paths get automatically set in the APK path and Test APK path input fields. If you are not using **Android Build for UI Testing** step, make sure the **App path** input points to the path of the APK or AAB file of your app and test suite.
​
7. Add one or more devices in the **Devices** step input.
​
8. Configure additional step inputs like **Debug logs** and **Test Configurations** and start your build.

## Troubleshooting

TO-DO: @rishabh

## 🧩 Get started

Add this step directly to your workflow in the [Bitrise Workflow Editor](https://devcenter.bitrise.io/steps-and-workflows/steps-and-workflows-index/).

You can also run this step directly with [Bitrise CLI](https://github.com/bitrise-io/bitrise).

## ⚙️ Configuration

<details>
<summary>Inputs</summary>

| Key | Description | Flags | Default |
| --- | --- | --- | --- |
| `app_apk_path` | Path of the app (.apk) file. | required | `$BITRISE_APK_PATH` |
| `testsuite_apk_path` | Path of the test suite (.apk) file . | required | `$BITRISE_TEST_APK_PATH` |
| `devices` | Name of one or more device-OS combination in new line. For example: <br /> `Samsung Galaxy S9 Plus-9.0` <br />`Google Pixel 3a-9.0` | required | `Samsung Galaxy S9 Plus-9.0` |
| `instrumentation_logs` | Generate instrumentation logs of the test session  |  | `true` |
| `network_logs` | Generate network logs of your Espresso test sessions to capture network traffic, latency, etc. |  | `false` |
| `device_logs` | Generate device logs (Android logcat) |  | `false` |
| `debug_screenshots` | Capture the screenshots of the test execution|  | `false` |
| `video_recording` | Record video of the test execution  |  | `true` |
| `project` | Project name of the tests |  |  |
| `project_notify_url` | A callback URL to enable BrowserStack notify about completion of build under a given project.   |  |  |
| `use_local` | Enable local testing to retrieve app data hosted on local/private servers  |  | `false` |
| `use_test_sharding` | Enable test sharding to split tests cases into different groups instead of running them sequentially. <br />Add the sharding value json here. Examples: **Input for auto strategy**: <br /> ```{"numberOfShards": 2}, "devices": ["Google Pixel 3-9.0"]``` <br /> **Input for package strategy**:```{"numberOfShards": 2, "mapping": [{"name": "Shard 1", "strategy": "package", "values": ["com.foo.login", "com.foo.logout"]}, {"name": "Shard 2", "strategy": "package", "values": ["com.foo.dashboard"]}]}```  **Input for class strategy**: ```{"numberOfShards": 2, "mapping": [{"name": "Shard 1", "strategy": "class", "values": ["com.foo.login.user", "com.foo.login.admin"]}, {"name": "Shard 2", "strategy": "class", "values": ["com.foo.logout.user"]}]}```|  |  |
| `clear_app_data` | Enable to clear app data after every test run|  | `false`  |
| `filter_test` | "Key-value pairs of filters to run tests from supported test filtering strategies: class, package, annotation, size <br /> Examples: **For class filtering strategy**: `class com.android.foo.ClassA, class com.android.foo.ClassB,class com.android.foo.ClassC` <br /> **For package filtering strategy**: `package com.android.foo` <br /> **For annotation filtering strategy**: `size small`,`size medium`,`size large`  |  |  |
| `use_single_runner_invocation` | Enable to run all tests in a single instrumentation process to reduce overall build time.  |  | `false`  |
| `use_mock_server` | Enable to mock a web server in your espresso tests to mock your API responses. Learn more. |  | `false` |
| `check_build_status` | Wait for BrowserStack to complete the execution and get the test results  |  | `true` |
| `api_params` |"New line separated variables, key and value seperated by `=` For example: `coverage=true` <br />`geoLocation=CN"` |  |  |

</details>

<details>
<summary>Outputs</summary>

| Environment Variable | Description |
| --- | --- |
| `$BROWSERSTACK_BUILD_URL` |BrowserStack Dashboard url for the executed build|
| `$BROWSERSTACK_BUILD_STATUS`| Status of the executed build. Check out the [test results guide](https://www.browserstack.com/docs/app-automate/espresso/view-test-results) to learn about available status  |

</details>
