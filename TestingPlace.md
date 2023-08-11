## Repositories

{% tabs %}
{% tab title="Gradle (Groovy)" %}
```groovy
repositories {
    // ...
    mavenCentral()
    maven { url 'https://mvn.lumine.io/repository/maven-public/' }
}
```
{% endtab %}

{% tab title="Gradle (Kotlin)" %}
```groovy
repositories {
    // ...
    mavenCentral()
    maven(url = "https://mvn.lumine.io/repository/maven-public/")
}
```
{% endtab %}

{% tab title="Maven" %}
```markup
<repositories>
    <!-- ... -->
    <repository>
        <id>nexus</id>
        <name>Lumine Releases</name>
        <url>https://mvn.lumine.io/repository/maven-public/</url>
    </repository>
</repositories>
```
{% endtab %}
{% endtabs %}
