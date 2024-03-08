# buildSrc
springboot와 kotlin을 사용해서 멀티모듈세팅을 하면서 의존성을 어떻게 관리해야 하는지에 대한 고민이 생겼고 buildSrc모듈을 사용해서 의존성관리와 버전관리를 해보자는 생각이 들었다. 이 글에서는 gradle의 buildSrc에 대해 알아보는 시간을 가져보겠습니다.

---

### buildSrc란?

라이브러리 버전관리를 좀 더 편리하게 하기 위해 buildSrc를 활용할 수 있다.

### 왜 사용하지?

buildSrc를 이용하면 build script를 더 쉽게 유지보수하고 가독성을 향상시킬 수 있습니다.

```
dependencies {
		/* kotlin */
		implementation(Dependencies.KOTLIN_JDK)
		implementation(Dependencies.KOTLIN_REFLECT)

		/* logging */
		implementation(Dependencies.LOGGING)
		testImplementation(Dependencies.LOGGING)
}
```

### 구현

구현하는 방법은 매우 간단하다.

먼저 buildSrc 디렉토리를 만들어준다, 그리고 그 안에 build.gradle.kts라는 파일을 만들어준다.

```
plugins {
    `kotlin-dsl`
}

repositories {
    mavenCentral()
}
```

build.gradle.kts 파일 안에 이렇게 기재해주고 빌드를 한 번 시키면 끝난다.

여기서 중요한 점은 setting.gradle.kts 파일에서 buildSrc모듈을 기재하지 않는다. 

그 이유는 개발자가 직접 사용하는 모듈이 아닌 의존성과 프로젝트 모듈을 위해 사용되는 모듈이기 때문이다.

이제 위처럼 작성하고 빌드를 마무리하면 

```
object PluginVersions {
    const val SPRING_BOOT_VERSION = "2.7.5"
    const val DEPENDENCY_MANAGER_VERSION = "1.1.0"
    const val JVM_VERSION = "1.7.22"
    const val SPRING_PLUGIN_VERSION = "1.7.22"
    const val JPA_PLUGIN_VERSION = "1.6.21"
    const val ALL_OPEN_VERSION = "1.6.21"
    const val KAPT_VERSION = "1.7.10"
}
```

위와 같이 PluginVersions와 같은 object 파일을 생성한다.

실제사용은 아래의 코드처럼 사용할 수 있습니다. 실제 버전을 작성하는 것이 아닌 buildSrc에서 선언한 변수가 들어가게 됩니다.

이런 식으로 사용함으로써 좀 더 유지보수 가능한 빌드도구 script가 만들어진 것을 확인할 수 있습니다.
