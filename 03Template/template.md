# 하위 클래스에서 구체적으로 처리하기.

템플릿이란 문자 모양으로 구멍이 뚫려있는 얇은 플라스틱 판을 말한다. 그 구멍을 따라 펜으로 그리면
손으로도 반듯한 문자를 쓸 수 있습니다 템플릿의 구멍을 보면 어떤 모양의 문자인지는 알 수 있지만 실제로
어떤 문자가 될지는 필기구에 의해 결정됩니다. 펜을 사용하면 펜으로 쓴 문자가 되고 연필을 사용하면 연필로 쓴 문자가 됩니다
그러나 어떤 기구를 사용해도 쓰여진 문자는 템플릿 구멍의 형태와 동일.

## Template Method 패턴이란?

템플릿의 기능을 가진 패턴

상위 클래스쪽에 템플릿에 해당하는 메서드가 정의되어 있고, 그 메소드의 정의 안에는 추상 메소드가 사용되고 있습니다.
따라서 상위 클래스의 프로그램만 보면 추상 메소드를 어떻게 호출하고 있는지 알 수 있지만 최종적으로 어떤 처리가 수행되는지는 알 수 없습니다

추상 메서드를 실제로 구현하는 것은 하위 클래스입니다 하위 클래스 측에서 메서드를 구현하면 구체적인 처리가 결정됩니다.
서로 다른 하위 클래스가 서로 다른 구현을 실행하면 서로 다른 처리가 실행될 것입니다. 그러나 어떤 하위 클래스에서 어떤 구현을 하더라도 처리의 큰 흐름은 상위 클래스에서 결정한 대로 이루어집니다.
이와 같이 상위 클래스에서 처리의 뼈대를 결정하고, 하위 클래스에서 그 구체적인 내용을 결정하는 디자인 패턴을 템플릿 패턴

## 등장인물

#### AbstractClass(추상 클래스)의 역할

AbstractClass는 템플릿 메서드를 구현합니다. 또한 그 템플릿 메소드에서 사용하고 있는 추상 메서드를 선언합니다.
이 추상 메서드는 하위 클래스인 ConcreateClass 역할에 의해 구현됩니다.
예제 프로그램에서는 AbstractDisplay

#### ConcreateClass(구현 클래스)의 역할

AbstractClass 역할에서 정의되어 있는 추상 메소드를 구체적으로 구현합니다 여기에서 구현한 메소드는 AbstractClass역의 템플릿 메소드에서 호출됩니다
예제 프로그램에서는 CharDispaly 클래스나 StringDisplay 클래스가 이역할을 합니다

### 독자의 사고를 넓히기 위한 힌트

#### 로직을 공통화할 수 있다.
템플릿메소드 패턴의 큰 이점은 로직을 공통화할 수 있다라는 점.

#### 상위 클래스와 하위 클래스의 연계
템플릿 메서드 패턴에서는 상위 클래스와 하위 클래스가 긴밀하게 연락을 취하며 작동하고 있습니다.
따라서 상위 클래스에서 선언된 추상 메소드를 실제로 하위 클래스에서 구현할 때에는 그 메소드가 어느 타이밍에서
호출되는지 이해해야 합니다. 상위 클래스의 소스 프로그램이 없으면 하위 클래스의 구현이 어렵습니다.

#### 하위 클래스를 상위 클래스와 동일시한다.
예제 프로그램 안에서는 CharDisplay의 인스턴스도, StringDisplay의 인스턴스도 AbstractDisplay 형의 변수에 대입하고 있습니다
그리고 display메소드를 호출하고 있습니다. 상위 클래스형의 변수가 있고, 그 변수에 하위 클래스형의 인스턴스가 대입된다고 가정합니다.
이때 instanceof 등으로 하위 클래스의 종류를 특정하지 않아도 프로그램이 작동하도록 만드는 것이 좋다.

**상위 클래스형의 변수에 하위 클래스의 어떠한 인스턴스를 대입해도 제대로 작동할 수 있도록 한다**

처리의 골격은 상위클래스에서 기술하고 구체적인 내용은 하위 클래스에서 수행하도록 작업한다.
어느 레벨에서 처리를 분해할지 어떤 처리를 상위 클래스에 두고 어떤 처리를 하위 클래스에 둘 것인지를 정한 메뉴얼은 없습니다
그것은 프로그램을 설계하는 사람의 몫입니다