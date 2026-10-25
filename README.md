# JarSplitter-Gradle

**JarSplitter-Gradle** - аналог [`Cutter`](https://forum.mcmodding.ru/resources/vyrezalka-2.198/) от JustAGod с полной поддержкой распила на клиент, сервер и дев билды.

# Пример подключения в `build.gradle`
```groovy
buildscript {
    repositories {
        ...
        maven { url 'https://jitpack.io' }
    }
    dependencies {
        ...
        classpath "com.github.LuxinfineTeam:JarSplitterGradle:plugin-SNAPSHOT"
    }
}

apply plugin: 'team.luxinfine.jarsplitter'

repositories {
    maven { url 'https://jitpack.io' }
}

dependencies {
    //Для 1.7.10 forge
    implementation 'com.github.LuxinfineTeam:JarSplitterGradle:api-1.7.10-SNAPSHOT'
    //Для 1.12.2 forge
    //implementation 'com.github.LuxinfineTeam:JarSplitterGradle:api-1.12.2-SNAPSHOT'
    //Для 1.21.1 neoforge
    //implementation 'com.github.LuxinfineTeam:JarSplitterGradle:api-1.21.1-neo-SNAPSHOT'
}
```

# Плагин предоставит Gradle таски:
- `buildClient` - сборка клиентской версии Jar
- `buildServer` - сборка серверной версии Jar
- `buildDev` - сборка DEV версии Jar. По сути, это сборка мода БЕЗ распила с деобфускацией майнкрафт маппингов. Да, можно получить такой jar и вручную, но таск чисто для удобства
- `buildAll` - сборка всех 3 версий Jar
