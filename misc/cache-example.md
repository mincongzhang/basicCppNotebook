```
class Cache {
private:
    bool m_compute;
    mutable int * m_cache;
    int m_value;

public:
    void initCache() {
        m_cache = new int [MAX_SIZE];        
    }
    
    bool updateValue(int index,int value) const {
        if(index<=MAX_SIZE && m_cache){
            m_cache[index] = value;
            return true;
        }
        
        return false;
    }
    
    getValue

};
```