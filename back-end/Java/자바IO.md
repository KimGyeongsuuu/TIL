# 자바IO
+ 자바 IO는 크게 byte단위 입출력과 문자 단위 입출력클래스로 나뉩니다.
    + byte단위 입출력클래스는 모두 InputStream과 OutputStream이라는 추상클래스를 상속받아 만들어집니다.
    + 문자(char)단위 입출력클래스는 모두 Reader와 Writer라는 추상클래스를 상속받아 만들어집니다.
+ 4가지 추상클래스(InputStream,OutputStreamReader,Reader,Writer)를 받아들이는 생성자가 있다면, 다양한 입출력방법을 제공하는 클래스입니다.
+ 4가지 클래스를 받아들이는 생성자가 없다면, 어디로부터 입력받을 것인지, 어디에 쓸것인지를 나타내는 클래스입니다.
+ 파일로 부터 입력받고 쓰기 위한 클래스 : FileInputStream, FileOutputStream, FileReader, FileWriter
+ 배열로 부터 입력받고 쓰기 위한 클래스 : ByteArrayInputStream, ByteArrayOutputStream, CharReader, CharWriter
    + 해당 클래스들은 어디로부터, 어디에라는 대상을 지정할 수 있는 IO클래스입니다. 이런 클래스를 장식대상 클래스라고 합니다.
+ DataInputStream, DataOutputStream같은 클래스를 보면 다양한 데이터 형을 입력받고 출력합니다.
+ PrintWriter는 다양하게 한줄 출력하는 pintln()메소드를 가지고있습니다.
+ BufferedReader는 한줄 입력받는 readLine()메소드를 가집니다.
이런 클래스들은 다양한 방식으로 입력하고, 출력하는 기능을 제공합니다. 
    + 이런 클래스를 장식하는 클래스라고 합니다.