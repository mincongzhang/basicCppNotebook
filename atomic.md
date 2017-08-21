```
#include <vector>
#include <iostream>
#include <thread>
#include <atomic>
#include <chrono>

int cnt = 0;
std::atomic<int> flag = {1};
void load()
{
    flag.load(std::memory_order_acquire);
    std::cout << "Load counter value is " << cnt << '\n';
}

void set(int i)
{
    //flag.load(std::memory_order_acquire); // will make the result bad 
    std::cout << "Load counter value is " << cnt << '\n';
    for (int n = 0; n < 1000; ++n) {
        cnt++;
        //std::this_thread::sleep_for(std::chrono::seconds(0.00002));
        if(i == 1) { std::cout << " " << cnt << std::endl;}
    }
    flag.store(1, std::memory_order_release);
}

int main()
{
    std::vector<std::thread> v;
    for (int n = 0; n < 10; ++n) {
        std::thread(set, n).join();
        std::thread(load).join();
    }

    std::cout << "Final counter value is " << cnt << '\n';

}
```


http://www.cplusplus.com/reference/atomic/atomic/load/ 

[http://en.cppreference.com/w/cpp/atomic/memory\_order](http://en.cppreference.com/w/cpp/atomic/memory_order)

