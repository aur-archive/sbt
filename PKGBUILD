# Maintainer: jpate <j.k.pate@sms.ed.ac.uk>
pkgname=sbt
pkgver=0.12.0
maintainer="jpate"
pkgrel=1
pkgdesc="Simple-build-tool: A build tool for Scala"
arch=('any')
url="https://github.com/harrah/xsbt/"
license=('New BSD License')
depends=( 'java-runtime' )
source=( "http://typesafe.artifactoryonline.com/typesafe/ivy-releases/org.scala-sbt/sbt-launch/$pkgver/sbt-launch.jar" )
noextract=('sbt-launch.jar')
md5sums=('69c2f0cdf38cfb1ca35dd3cbd8f18b2f')

build() {
  cd $startdir

  mkdir -p $pkgdir/usr/bin/
  mkdir -p $pkgdir/usr/share/sbt/
  cp $srcdir/sbt-launch.jar $pkgdir/usr/share/sbt/

  cat > $pkgdir/usr/bin/sbt <<EOF
#!/bin/sh
if [[ -n "\$JAVA_HOME" ]]; then
  JAVA_CMD=\$JAVA_HOME/bin/java
else
  JAVA_CMD=\$(which java)
fi
if [[ -z "\$JAVA_ARGS" ]]; then
  JAVA_ARGS=""
fi
EOF
  echo "\$JAVA_CMD \$JAVA_ARGS \${SBT_OPTS} -jar /usr/share/sbt/sbt-launch.jar  \"\$@\"" >> $pkgdir/usr/bin/sbt

  chmod a+x $pkgdir/usr/bin/sbt
}

