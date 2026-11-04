# Сборка Litum 4.2.5 TEST

Сборка выполняется на GitHub Actions из полного исходного проекта, а не из готового APK.

## Что уже настроено

- Android Gradle Plugin 8.5.2
- Gradle Wrapper 8.7
- JDK 17
- Android SDK / Build Tools 34
- applicationId: com.litum.brochure.test
- versionCode: 46
- versionName: 4.2.5-TEST
- Min SDK 21, Target SDK 34
- Отдельный постоянный тестовый ключ подписи litum-test
- Проверки JavaScript, CIEDE2000, цветового каталога, выравнивания и APK-подписи

## Действия один раз

1. Загрузить архив Litum_Spravochnik_4_2_5_TEST_sources.zip в каталог build-input/ этого репозитория. Путь должен быть ровно build-input/Litum_Spravochnik_4_2_5_TEST_sources.zip.
2. В GitHub открыть Settings → Secrets and variables → Actions.
3. Добавить секрет LITUM_TEST_KEYSTORE_BASE64 — полное содержимое файла LITUM_TEST_KEYSTORE_BASE64.txt из закрытой папки с тестовым ключом.
4. Добавить секрет LITUM_TEST_SIGNING_PASSWORD — содержимое файла LITUM_TEST_SIGNING_PASSWORD.txt.
5. Не загружать ключ, пароль или keystore.properties в публичный репозиторий.

После загрузки ZIP workflow запускается автоматически. Результат находится в Actions → Build Litum 4.2.5 TEST APK → Artifacts → Litum-4.2.5-TEST-APK.

## Для следующих сборок

Использовать тот же тестовый ключ и те же Secrets. Не генерировать новый ключ: иначе Android не позволит обновлять установленную тестовую сборку поверх.

## Безопасность

Тестовый ключ отличается от производственного lit.p12 версии 4.1.1. Он не включён в репозиторий. Основной пакет com.litum.brochure и его подпись не меняются.