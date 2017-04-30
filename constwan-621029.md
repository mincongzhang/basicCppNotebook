### const int \*, const int \* const, and int const \*

##### The "Clockwise/Spiral Rule": Read from right to left

```
int * - pointer to int
int const * - pointer to const int
int * const - const pointer to int
int const * const - const pointer to const int

Now the first const can be on either side of the type so:
const int * == int const *
const int * const == int const * const
```

##### const int \* \(int const \*\) - pointer to const int

The pointer can be changed:

```
    const int a = 1;
    const int * ptr = &a;
    std::cout<<*ptr<<std::endl;

    const int b = 2;
    ptr = &b;
    std::cout<<*ptr<<std::endl;
```

#### int \* const - const pointer to int

```
    int a = 1;
    int * const ptr = &a;
    std::cout<<*ptr<<std::endl;

    //int b = 2;
    //ptr = &b;

    a = 3;
    std::cout<<*ptr<<std::endl;
```

#### const member function

```
class Cache {
private:
    int * m_cache;
public:
    Cache(){
        m_cache = new int [100];
    }

    ~Cache(){
        delete [] m_cache;
    }

    bool update(int index,int value) const {
        if(index <= 100){
            m_cache[index] = value;
            std::cout<<"index:["<<index<<"] value updated to ["<<m_cache[index]<<"]"<<std::endl;
            return true;
        } 

        return false;
    }
};
```

In the example, const member function in C style should be like:

```
    bool update(const Cache * this, int index,int value){
        //...
    }
```

**and m\_cache should be run like **`int * const m_cache;`**, it's "const pointer to int", and the value can be changed, so no compile error**

#### const Cache c???

```
int main(){
    const Cache c;
    c.update(1,1);
}
```

