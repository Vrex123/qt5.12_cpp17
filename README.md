Straighforward Dockefile with Qt installed in it to use with CI for building Qt projects with GCC

Pre-built Docker image can be found in [Docker repo](https://hub.docker.com/r/vrex141/qt5.12_cpp17)

## Usage
For example, here is how it can be used in Jenkins
```Groovy
  stage('Build Linux binary') {
    agent {
      docker {
        image 'vrex141/qt5.12_cpp17'
      }
    }
    steps {
      sh 'qmake workplace.pro -spec linux-g++ CONFIG+=qtquickcompiler && /usr/bin/make qmake_all'
      sh 'make'
      sh 'make clean'
      stash includes: 'bin/**', name: 'linux_binary'
    }
  }
```

## Versions
- Ubuntu 18.04
- Qt 5.12.4

