---
title: GitHub Enterprise Serverで脆弱性のある依存関係に対するアラートを有効化する
intro: '{% data variables.product.product_location_enterprise %} を {% data variables.product.prodname_ghe_cloud %} に接続し、インスタンス内のリポジトリの脆弱な依存関係に対して{% if currentVersion ver_gt "enterprise-server@2.21" %}{% data variables.product.prodname_dependabot_short %}{% else %}セキュリティ{% endif %}アラートを有効にすることができます。'
redirect_from:
  - /enterprise/admin/installation/enabling-security-alerts-for-vulnerable-dependencies-on-github-enterprise-server
  - /enterprise/admin/configuration/enabling-security-alerts-for-vulnerable-dependencies-on-github-enterprise-server
  - /enterprise/admin/configuration/enabling-alerts-for-vulnerable-dependencies-on-github-enterprise-server
permissions: '接続された {% data variables.product.prodname_ghe_cloud %} Organization または Enterprise アカウントの所有者でもある {% data variables.product.prodname_ghe_server %} のサイト管理者は、{% data variables.product.prodname_ghe_server %} の脆弱性のある依存関係に対して{% if currentVersion ver_gt "enterprise-server@2.21" %}{% data variables.product.prodname_dependabot_short %}{% else %} セキュリティ{% endif %}アラートを有効にできます。'
versions:
  enterprise-server: '*'
---

### {% data variables.product.prodname_ghe_server %} 上の脆弱性のある依存関係に対するアラートについて

{% data reusables.repositories.tracks-vulnerabilities %} 詳しい情報については、「[脆弱性のある依存関係に対するアラートについて](/github/managing-security-vulnerabilities/about-alerts-for-vulnerable-dependencies)」を参照してください。

{% data variables.product.product_location_enterprise %} を {% data variables.product.prodname_dotcom_the_website %} に接続し、脆弱性データをインスタンスに同期して、脆弱性のある依存関係を持つリポジトリで {% if currentVersion ver_gt "enterprise-server@2.21" %}{% data variables.product.prodname_dependabot_short %}{% else %}セキュリティ{% endif %}アラートを生成できます。

{% data variables.product.product_location_enterprise %} を {% data variables.product.prodname_dotcom_the_website %} に接続し、脆弱性のある依存関係に対して {% if currentVersion ver_gt "enterprise-server@2.21" %}{% data variables.product.prodname_dependabot_short %}{% else %}セキュリティ{% endif %}アラートを有効化すると、脆弱性データは 1 時間に 1 回 {% data variables.product.prodname_dotcom_the_website %} からインスタンスに同期されます。 また、脆弱性データはいつでも手動で同期することができます。 {% data variables.product.product_location_enterprise %} からのコードまたはコードに関する情報は、{% data variables.product.prodname_dotcom_the_website %} にアップロードされません。

{% if currentVersion ver_gt "enterprise-server@2.21" %}When {% data variables.product.product_location_enterprise %} receives information about a vulnerability, it will identify repositories in your instance that use the affected version of the dependency and send {% data variables.product.prodname_dependabot_short %} alerts. You can customize how you receive {% data variables.product.prodname_dependabot_short %} alerts. For more information, see "[Configuring notifications for vulnerable dependencies](/github/managing-security-vulnerabilities/configuring-notifications-for-vulnerable-dependencies/#configuring-notifications-for-github-dependabot-alerts)."
{% endif %}

{% if currentVersion == "enterprise-server@2.21" %}When {% data variables.product.product_location_enterprise %} receives information about a vulnerability, it will identify repositories in your instance that use the affected version of the dependency and send security alerts. You can customize how you receive security alerts. For more information, see "[Configuring notifications for vulnerable dependencies](/github/managing-security-vulnerabilities/configuring-notifications-for-vulnerable-dependencies/#configuring-notifications-for-security-alerts)."
{% endif %}

{% if currentVersion ver_lt "enterprise-server@2.21" %}When {% data variables.product.product_location_enterprise %} receives information about a vulnerability, it will identify repositories in your instance that use the affected version of the dependency and send security alerts. You can customize how you receive security alerts. 詳しい情報については「[通知の配信方法を選択する](/github/receiving-notifications-about-activity-on-github/choosing-the-delivery-method-for-your-notifications#choosing-the-delivery-method-for-security-alerts-for-vulnerable-dependencies)」を参照してください。
{% endif %}

{% if currentVersion ver_gt "enterprise-server@2.21" %}
### {% data variables.product.prodname_ghe_server %} 上の脆弱性のある依存関係に対して {% data variables.product.prodname_dependabot_short %} アラートを有効化にする
{% else %}
### {% data variables.product.prodname_ghe_server %}で脆弱性のある依存関係に対するアラートを有効化する
{% endif %}

{% data variables.product.product_location_enterprise %} 上の脆弱性のある依存関係に対する {% if currentVersion ver_gt "enterprise-server@2.21" %}{% data variables.product.prodname_dependabot_short %}{% else %} セキュリティ{% endif %}アラートを有効にする前に、{% data variables.product.product_location_enterprise %} を {% data variables.product.prodname_dotcom_the_website %} に接続する必要があります。 詳細は、「[{% data variables.product.prodname_ghe_server %}を{% data variables.product.prodname_ghe_cloud %}に接続する](/enterprise/{{ currentVersion }}/admin/guides/installation/connecting-github-enterprise-server-to-github-enterprise-cloud)」を参照してください。

{% if currentVersion ver_gt "enterprise-server@2.20" %}

{% if currentVersion ver_gt "enterprise-server@2.21" %}メールの過負荷を避けるため、最初の数日間は {% data variables.product.prodname_dependabot_short %} アラートを通知なしに設定することをお勧めします。 数日後、通知を有効化すれば、通常どおり {% data variables.product.prodname_dependabot_short %} アラートを受信できます。{% endif %}

{% if currentVersion == "enterprise-server@2.21" %}メールの過負荷を避けるため、最初の数日間はセキュリティアラートを通知なしに設定することをお勧めします。 数日後、通知を有効化すれば、通常どおりセキュリティアラートを受信できます。{% endif %}

{% endif %}

{% data reusables.enterprise_site_admin_settings.sign-in %}
1. 管理シェルで、{% data variables.product.product_location_enterprise %} の脆弱性のある依存関係に対する {% if currentVersion ver_gt "enterprise-server@2.21" %}{% data variables.product.prodname_dependabot_short %}{% else %}セキュリティ{% endif %}アラートを有効にします。
 ``` shell
$ ghe-dep-graph-enable
```
   {% note %}

   **Note**: For more information about enabling access to the administrative shell via SSH, see "[Accessing the administrative shell (SSH)](/enterprise/{{ currentVersion }}/admin/configuration/accessing-the-administrative-shell-ssh)."

   {% endnote %}

3. 次に、

{% data variables.product.prodname_ghe_server %}.
{% data reusables.enterprise_site_admin_settings.access-settings %}
{% data reusables.enterprise_site_admin_settings.business %}
{% data reusables.enterprise-accounts.settings-tab %}
{% data reusables.enterprise-accounts.github-connect-tab %}{% if currentVersion ver_gt "enterprise-server@2.20" %}
5. [Repositories can be scanned for vulnerabilities] で、ドロップダウンメニューを使用して、[**Enabled without notifications**] を選択します。 必要に応じて、通知を含むアラートを有効化にするには、[**Enabled with notifications**] を選択します。{% else %}
5. 「Repositories can be scanned for vulnerabilities」で、ドロップダウンメニューを使用して「**Enabled**」を選択します。
{% endif %}
   ![脆弱性に対するリポジトリのスキャンを有効化するドロップダウンメニュー](/assets/images/enterprise/site-admin-settings/enable-vulnerability-scanning-in-repositories.png)

### {% data variables.product.prodname_ghe_server %}で脆弱性のある依存関係を表示する

{% data variables.product.product_location_enterprise %}ですべての脆弱性を表示し、{% data variables.product.prodname_dotcom_the_website %}から脆弱性データを手動で同期して、リストを更新することができます。

{% data reusables.enterprise_site_admin_settings.access-settings %}
2. 左サイドバーで [**Vulnerabilities**] をクリックします。 ![サイト管理サイドバーの [Vulnerabilities] タブ](/assets/images/enterprise/business-accounts/vulnerabilities-tab.png)
3. 脆弱性データを同期するには、[**Sync Vulnerabilities now**] をクリックします。 ![[Sync vulnerabilities now] ボタン](/assets/images/enterprise/site-admin-settings/sync-vulnerabilities-button.png)
