# SkyCraft JarSplitterGradle (binary fork)

Этот репозиторий публикует готовый **JarSplitterGradle-v1.1.9.jar** как Maven-артефакт SkyCraft.

> В репозитории нет Java/Groovy-исходников самого плагина. Изменение `build.gradle` меняет упаковку и координаты публикации, **но не логику** разделения на CLIENT/SERVER.

## Сборка / локальная публикация

Используется Gradle 8.14.3 (см. `gradle/wrapper/gradle-wrapper.properties`). В репозитории не хранится `gradle-wrapper.jar`; для команды `./gradlew` требуется восстановить wrapper либо использовать установленный Gradle.

```powershell
gradle publishToMavenLocal
```

Публикуются координаты:
```text
com.github.denis128873:JarSplitterGradle:v1.1.9
```

Для этой локальной публикации в потребляющем проекте можно добавить `mavenLocal()` в `buildscript.repositories` и зависимость на эти координаты, после чего применить `team.luxinfine.jarsplitter`. Совместимость с версией MultiJavaForgePlugin и публикацию JitPack необходимо проверять отдельно.

## Разделение сторон

В существующем бинарном плагине заявлены задачи:

- `buildClient` — клиентские классы и общие зависимости.
- `buildServer` — серверные классы и общие зависимости.
- `buildDev` — несекционированная dev-сборка.
- `buildAll` — все три варианта.

Для SKC-CLR должны получаться два самостоятельных артефакта:

```text
SKC-CLR-1.7.10-10.2-client.jar
SKC-CLR-1.7.10-10.2-server.jar
```

Проверяйте содержимое обоих JAR через `jar tf`; простое переименование `-j8.jar` не разделяет классы.

## Зависимости плагина

Maven POM перечисляет ASM Tree 9.10.1 и fastutil 8.5.16 как runtime-зависимости. Другие совместимые API-зависимости (включая аннотации `@Environment`) необходимо объявлять в самих модах отдельно.
