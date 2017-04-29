```
class Cache {
private:
    bool m_compute;
    int * m_cache;
    mutable int m_value;
    friend static int computeValue();

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
    
    int getValue() const {
        if(m_compute){
            m_value = computeValue();
            return m_value;
        }
        
        return m_value;        
    }

};
```