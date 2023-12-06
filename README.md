# Example of a jetty-parent-pom
The goal is to reduce copy/paste of the same content in multiple repositories.
having a common set of plugins version. Updated monthly via dependabot with maybe a monthly release of this parent.
We don't really need to copy/paste the SAME plugins versions in multiple poms and having to run dependabot in so many places.

# Jdk setup

Per default the pom configure projects to use Jdk 1.8, (enforce plugins as well)
If you need to be 11 as minimum, just use `<jdk.version.minimum>17</jdk.version.minimum>`
This single property will be used for:
- `<maven.compiler.source>${jdk.version.minimum}</maven.compiler.source>`
- `<maven.compiler.target>${jdk.version.minimum}</maven.compiler.target>`
- `<maven.compiler.release>${jdk.version.minimum}</maven.compiler.release>` (only for jdk9+)

If you need some special trick such build should use 11 but I need 8 as produced bytecode, just use:
- `<jdk.version.minimum>11</jdk.version.minimum>`
- `<maven.compiler.release>8</maven.compiler.release>`

There is no need to configure target and release as it will be ignored by compiler (you can of course but it is just ignored)


# Maven setup
The property `<maven.version.minimum>3.9</maven.version.minimum>` will configure the enforcer to enforce this as minimum Maven version to use


