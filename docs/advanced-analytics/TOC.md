# 概觀

## [什麼是 SQL Server 機器學習服務？](what-is-sql-server-machine-learning.md)
### [資料庫內分析](r/sql-server-r-services.md)
### [獨立伺服器](r/r-server-standalone.md)
## [新功能](what-s-new-in-sql-server-machine-learning-services.md)
## [不同版本的功能](r/differences-in-r-features-between-editions-of-sql-server.md)

# [架構](architecture-overview-machine-learning.md)
## [R](r/architecture-overview-sql-server-r.md)
### [R 互通性](r/r-interoperability-in-sql-server.md)
### [支援 R 整合的元件](r/new-components-in-sql-server-to-support-r.md)
### [R 的安全性](r/security-overview-sql-server-r.md)
## [Python](python/architecture-overview-sql-server-python.md)
### [機器學習服務中的 Python](python/sql-server-python-services.md)
### [Python 互通性](python/python-interoperability.md)
### [支援 Python 的元件](python/new-components-in-sql-server-to-support-python-integration.md)
### [Python 安全性](python/security-overview-sql-server-python-services.md)
<!-- ### [How To Create a Resource Pool for Python](python/how-to-create-a-resource-pool-for-python.md)-->
<!-- ### [Extended Events for Python](python/extended-events-for-python.md)-->
<!-- ### [DMVs for Python](python/dmvs-for-python.md)-->
<!-- ### [Resource Governance for Python](python/resource-governance-for-python.md)-->

# Install 

## [資料庫內分析](install/sql-machine-learning-services-windows-install.md)
## [獨立伺服器](install/sql-machine-learning-standalone-windows-install.md)
## [預先訓練模型](r/install-pretrained-models-sql-server.md)
## SQL Server 2016
### [R Services (資料庫內)](install/sql-r-services-windows-install.md)
### [R Server (獨立式)](install/sql-r-standalone-windows-install.md)
## [命令提示字元安裝程式](install/sql-ml-component-commandline-install.md)
## [離線安裝程式 (不連線到網際網路)](install/sql-ml-component-install-without-internet-access.md)
## [升級 R 與 Python](r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)
## [設定 R 工具](r/set-up-a-data-science-client.md)
## [設定 Python 工具](python/setup-python-client-tools-sql.md)

# [教學課程、範例、解決方案](tutorials/machine-learning-services-tutorials.md)

## [R](tutorials/sql-server-r-tutorials.md)
### [R：在 Transact-SQL 中使用 R 程式碼](tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
#### [處理輸入及輸出](tutorials/rtsql-working-with-inputs-and-outputs.md)
#### [R 與 SQL 資料類型及資料物件](tutorials/rtsql-r-and-sql-data-types-and-data-objects.md)
#### [R 函式搭配 SQL Server 資料](tutorials/rtsql-using-r-functions-with-sql-server-data.md)
#### [建立預測模型](tutorials/rtsql-create-a-predictive-model-r.md)
#### [從模型預測及繪製](tutorials/rtsql-predict-and-plot-from-model.md)
### [R：資料科學詳細逐步解說](tutorials/walkthrough-data-science-end-to-end-walkthrough.md)
#### [資料科學逐步解說的必要條件](tutorials/walkthrough-prerequisites-for-data-science-walkthroughs.md)
#### [準備資料](tutorials/walkthrough-prepare-the-data.md)
#### [使用 SQL 瀏覽資料](tutorials/walkthrough-view-and-explore-the-data.md)
#### [使用 R 摘要資料](tutorials/walkthrough-view-and-summarize-data-using-r.md)
#### [使用 R 建立圖表及繪圖](tutorials/walkthrough-create-graphs-and-plots-using-r.md)
#### [使用 SQL 及 R 建立資料特徵](tutorials/walkthrough-create-data-features.md)
#### [建立及儲存模型](tutorials/walkthrough-build-and-save-the-model.md)
#### [部署及使用模型](tutorials/walkthrough-deploy-and-use-the-model.md)
### [R：使用 RevoScaleR 深入鑽研資料科學](tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
#### [使用 SQL Server 資料](tutorials/deepdive-work-with-sql-server-data-using-r.md)
#### [使用 RxSqlServerData 建立 SQL Server 資料物件](tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)
#### [查詢及修改 SQL Server 資料](tutorials/deepdive-query-and-modify-the-sql-server-data.md)
#### [定義及使用計算內容](tutorials/deepdive-define-and-use-compute-contexts.md)
#### [建立及執行 R 指令碼](tutorials/deepdive-create-and-run-r-scripts.md)
#### [使用 R 製作 SQL Server 資料的圖表](tutorials/deepdive-visualize-sql-server-data-using-r.md)
#### [建立模型](tutorials/deepdive-create-models.md)
#### [為新資料評分](tutorials/deepdive-score-new-data.md)
#### [使用 R 轉換資料](tutorials/deepdive-transform-data-using-r.md)
#### [使用 rxImport 將資料載入記憶體](tutorials/deepdive-load-data-into-memory-using-rximport.md)
#### [使用 rxDataStep 建立新的 SQL Server 資料表](tutorials/deepdive-create-new-sql-server-table-using-rxdatastep.md)
#### [使用 rxDataStep 執行區塊處理分析](tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)
#### [分析本機計算內容中的資料](tutorials/deepdive-analyze-data-in-local-compute-context.md)
#### [在 SQL Server 與 XDF 檔案之間移動資料](tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)
#### [建立簡單的模擬](tutorials/deepdive-create-a-simple-simulation.md)
### [R：適用於 SQL 開發人員的資料庫內分析](tutorials/sqldev-in-database-r-for-sql-developers.md)
#### [步驟 1︰下載範例資料](tutorials/sqldev-download-the-sample-data.md)
#### [步驟 2︰使用 PowerShell 將資料匯入 SQL Server](r/sqldev-import-data-to-sql-server-using-powershell.md)
#### [步驟 3：瀏覽及視覺化資料](tutorials/sqldev-explore-and-visualize-the-data.md)
#### [步驟 4︰使用 T-SQL 建立資料特徵](tutorials/sqldev-create-data-features-using-t-sql.md)
#### [步驟 5︰使用 T-SQL 訓練及儲存模型](r/sqldev-train-and-save-a-model-using-t-sql.md)
#### [步驟 6︰執行模型](tutorials/sqldev-operationalize-the-model.md)

## [Python](tutorials/sql-server-python-tutorials.md)
### [Python：使用 T-SQL 執行 Python](tutorials/run-python-using-t-sql.md)
#### [將 Python 包裝到預存程序中](tutorials/wrap-python-in-tsql-stored-procedure.md)
#### [從 SQL Server 中的 Python 模型訓練及計分](tutorials/train-score-using-python-in-tsql.md)
#### [在 SQL Server 計算內容中使用 revoscalepy 建立模型](tutorials/use-python-revoscalepy-to-create-model.md)
### [Python：適用於 SQL 開發人員的資料庫內分析](tutorials/sqldev-in-database-python-for-sql-developers.md)
#### [下載範例資料](tutorials/sqldev-py1-download-the-sample-data.md)
#### [將資料匯入 SQL Server](tutorials/sqldev-py2-import-data-to-sql-server-using-powershell.md)
#### [探索及視覺化資料](tutorials/sqldev-py3-explore-and-visualize-the-data.md)
#### [使用 T-SQL 建立資料特徵](tutorials/sqldev-py4-create-data-features-using-t-sql.md)
#### [訓練及儲存](tutorials/sqldev-py5-train-and-save-a-model-using-t-sql.md)
#### [執行模型](tutorials/sqldev-py6-operationalize-the-model.md)
## [範例](https://github.com/Microsoft/sql-server-samples)
## [方案](tutorials/data-science-scenarios-and-solution-templates.md)

# [操作說明](r/sql-server-machine-learning-tasks.md)

## [套件管理](r/r-package-management-for-sql-server-r-services.md)
### [預設封裝](r/installing-and-managing-r-packages.md)
### [取得封裝資訊](r/determine-which-packages-are-installed-on-sql-server.md)
### [安裝新的 R 封裝](r/install-additional-r-packages-on-sql-server.md)
### [安裝新的 Python 封裝](python/install-additional-python-packages-on-sql-server.md)
### 僅限 R
#### [啟用遠端 R 封裝管理](r/r-package-how-to-enable-or-disable.md)
#### [適用於 R 封裝管理的 RevoScaleR 函式](r/use-revoscaler-to-manage-r-packages.md)
#### [R 封裝同步處理](r/package-install-uninstall-and-sync.md)
#### [本機 R 封裝存放庫的 miniCRAN](r/create-a-local-package-repository-using-minicran.md)
#### [R「使用者程式庫」的因應措施](r/packages-installed-in-user-libraries.md)

## 資料探索及模型化
### [R 程式庫和資料類型](r/r-libraries-and-data-types.md)
### [Python 程式庫和資料類型](python/python-libraries-and-data-types.md)
### [原生評分](sql-native-scoring.md)
### [即時評分](real-time-scoring.md)
### [R 預測模型](r/data-exploration-and-predictive-modeling-with-r.md)
### [如何執行即時或原生評分](r/how-to-do-realtime-scoring.md)
### [使用 ODBC 載入 R 物件](r/save-and-load-r-objects-from-sql-server-using-odbc.md)
### [轉換 R 程式碼以在 Machine Learning 服務中使用](r/converting-r-code-for-use-in-sql-server.md)
### [使用 rxExecBy 建立多個模型](r/creating-multiple-models-using-rxexecby.md)
### [在 R 中使用 OLAP Cube 的資料](r/using-data-from-olap-cubes-in-r.md)
### [使用 sqlrutils 建立預存程序](r/how-to-create-a-stored-procedure-using-sqlrutils.md)

## 效能
### [R 效能微調 - 概觀](r/sql-server-r-services-performance-tuning.md)
### [R 效能微調 - SQL Server 組態](r/sql-server-configuration-r-services.md)
### [R 效能微調 - R 和資料最佳化](r/r-and-data-optimization-r-services.md)
### [R 效能微調 - 結果](r/performance-case-study-r-services.md)
### [使用 R 程式碼剖析函式](r/using-r-code-profiling-functions.md)

## 系統管理
### [設定及管理 R](r/configuration-sql-server-r-services.md)
### [Machine Learning 服務的進階組態選項](r/configure-and-manage-advanced-analytics-extensions.md)
### [SQL Server 中 R 執行階段的安全性考量](r/security-considerations-for-the-r-runtime-in-sql-server.md)
### [修改 SQL Server Machine Learning 服務的使用者帳戶集區](r/modify-the-user-account-pool-for-sql-server-r-services.md)
### [新增 SQLRUserGroup 作為資料庫使用者](r/add-sqlrusergroup-to-database.md)
### [使用 Web 服務部署及取用模型](operationalization-with-mrsdeploy.md)
### [管理與監控解決方案](r/managing-and-monitoring-r-solutions.md
### [Machine Learning 服務的資源管理](r/resource-governance-for-r-services.md)
### [建立機器學習的資源集區](r/how-to-create-a-resource-pool-for-r.md)
### [Machine Learning 服務的擴充事件](r/extended-events-for-sql-server-r-services.md)
### [監視 PREDICT 陳述式的擴充事件](xe-event-predict-tsql.md)
### [Machine Learning 服務的 DMV](r/dmvs-for-sql-server-r-services.md)
### [使用 R 程式碼剖析函式](r/using-r-code-profiling-functions.md)
### [使用 Management Studio 中的自訂報表監視 Machine Learning 服務](r/monitor-r-services-using-custom-reports-in-management-studio.md)

# [參考](r/machine-learning-services-r-reference.md)

## [MicrosoftML](using-the-microsoftml-package.md)
## [RevoScaleR](r/revoscaler-overview.md)
### [適用於 SQL Server 資料的 ScaleR 函式](r/scaler-functions-for-working-with-sql-server-data.md)
## [SqlRUtils](r/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)
## [OlapR](r/how-to-create-mdx-queries-using-olapr.md)
## [revoscalepy](python/what-is-revoscalepy.md)

# 資源

## [已知問題](known-issues-for-sql-server-machine-learning-services.md)
## [版本資訊](https://docs.microsoft.com/sql/sql-server/sql-server-2017-release-notes)
## [新文章及更新的文章](new-updated-advanced-analytics.md)

## [安裝和疑難排解提示](machine-learning-troubleshooting-faq.md)
### [設定虛擬機器](r/installing-sql-server-r-services-on-an-azure-virtual-machine.md)
### [疑難排解的資料收集](data-collection-ml-troubleshooting-process.md)
### [升級與安裝的常見問題集](r/upgrade-and-installation-faq-sql-server-r-services.md)
### [外部指令碼執行的常見問題](common-issues-external-script-execution.md)

## 部落格
### [[SQL Server]](https://blogs.technet.microsoft.com/dataplatforminsider/)
### [R Server](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/)
### [機器學習服務](https://blogs.technet.microsoft.com/machinelearning/)

## 意見反應論壇
### [[SQL Server]](https://social.msdn.microsoft.com/Forums/sqlserver/home?category=sqlserver)
### [Microsoft R Server](https://social.msdn.microsoft.com/Forums/home?forum=MicrosoftR)
