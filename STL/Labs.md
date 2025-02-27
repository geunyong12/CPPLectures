# 프로그램 실습

* 클래스 텦플릿 ``vector``의 정의가 있는 C++ 표준 라이브러리 해터 파일 vector의 내용 일부
```c++
namespace std {
template <class Type, class Allocator = allocator<Type>>
class vector {
public:
    typedef T                                        value_type;
    typedef typename allocator_type::size_type       size_type;
    ...
    vector() noexcept(is_nothrow_default_constructible<allocator_type>::value);
    ~vector();
    // functions

    void push_back(const value_type& x);
    void push_back(value_type&& x);

    // operator
    vector& operator=(const vector& x);
    vector& operator=(vector&& x)
            noexcept(
             allocator_type::propagate_on_container_move_assignment::value ||
             allocator_type::is_always_equal::value); // C++17
    void assign(size_type n, const value_type& u);
    ...
    iterator begin() noexcept;
    iterator end() noexcept;
    ...
    reference front();
    reference back();
    패ㅑd resize(size_type sz);
    value_type* data() noexcept:
    ...
    };

} // namespace std
```


1.  클래스 템플릿 ``vector``를 사용한 프로그램이다. 프로그램 수행 결과를 예측하고 실행 결과의 비교하고 vector 분석하라.

```c++
#include <vector>
#include <iostream>

int main()
{
  
  using namespace std;
  vector<int> v1, v2, v3;

  v1.push_back(10);
  v1.push_back(20);
  v1.push_back(30);
  v1.push_back(40);
  v1.push_back(50);

  cout << "v1 = ";
  for (auto& v : v1){
     cout << v << " ";
  }
  cout << endl;

  v2.assign(v1.begin(), v1.end());
  cout << "v2 = ";
  for (auto& v : v2){
     cout << v << " ";
  }
   cout << endl;

   v3.assign(3, 6);
   cout << "v3 = ";
   for (auto& v : v3){
       cout << v << " ";
   }
   cout << endl;

   v3.assign({ 5, 6, 7 });
   for (auto& v : v3){
      cout << v << " ";
  }
  cout << endl;
  
  int &i = v1.at(0);
  
  cout << "v1 첫 번째 원소의 값:  " << i << endl; 

  if(v1 == v2) cout << "v1과 v2는 같다." << endl;
  else cout << "v1과 v2는 다르다" << endl;
  
  i = 80;
  const int &j = v1.at(0);
  
  cout << "값을 변경 후 v1 첫 번째 원소의 값:  " << j << endl; 

  if(v1 == v2) cout << "v1과 v2는 같다." << endl;
  else cout << "v1과 v2는 다르다" << endl;
}
```

2. 아래의 링크를 참조하여 vector 클래스의 다른 멤버 함수와 연산자를 활용한 프로그램을 작성하라.

https://learn.microsoft.com/ko-kr/cpp/standard-library/vector-operators?view=msvc-170 




