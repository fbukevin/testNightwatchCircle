
nightwatch 基於 selenium

要先下載 selenium-standalone-server-{version}.jar
然後手動或設定自動啟動 selenium server: java -jar selenium-standalone-server-{version}.jar
但是他好像內建不支援 chrome
要另外設定：https://github.com/nightwatchjs/nightwatch/wiki/chrome-setup
nightwatch.js 中只要這樣寫就是預設使用 chrome:

```
{
  "src_folders": ["test/nightwatches.js"],
  "output_folder": "reports",
  "selenium": {
    "start_process": true,
    "server_path": "bin/selenium-server-standalone-2.52.0.jar",
    "host": "127.0.0.1",
    "port": 9515,
    "cli_args": {
      "webdriver.chrome.driver": "./bin/chromedriver"
    }
  },
  "test_settings":{
    "default": {
      "launch_url": "http://localhost",
      "selenium_port": 9515,
      "selenium_host": "localhost",
      "silent": false,
      "screenshots":{
        "enabled": true,
        "path": "log"
      },
      "desiredCapabilities":{
        "browserName": "chrome",
        "javascriptEnable": true,
        "acceptSslCerts": true
      }
    }
  }
}
```

安裝 nightwatch: `sudo npm install nightwatch -g`

在 webstorm 中測試時，要先啟動你的 app server，在執行測試

