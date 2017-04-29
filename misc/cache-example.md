```
class Cache {
private:
    bool m_compute;
    int * m_cache;
    mutable int m_value;
    friend static int computeValue();

public:
    Cache(Cache & c){
        m_compute = c.m_compute;
        m_value = c.m_value;
        initCache();
        memcpy(c.m_cache,m_cache,MAX_SIZE*sizeof(int))
    }
    
    void initCache() {
        if(m_cache) delete [] m_cache;
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



