## Question 1
```
Round 1:
* 1 coding question with multiple parts. I solved 4 parts with working code and passed all test cases.
* 1 hour.
* Communication is also judged.
* Part 1: Design and code an interleaving iterator. Given 2 arrays output the elements in interleaving order.
* [1,2,3] [4,5,6] -> [1,4,2,5,3,6]
* Part 2: Design a range-based iterator with a given start, end and step value.
* (1, 10, 2) -> [1,3,5,7,9]
* Part 3: Design interleaving iterator with a list of iterators
* Part 4: Add a filter function to interleaving iterators
```

## Solution Self
```C++
class InterLeavingIterator{
    private:
        int i1,i2;
        int n1,n2;
        vector<int>& v1;
        vector<int>& v2;
    public:
        InterLeavingIterator(vector<int>& v1Input, vector<int>& v2Input):v1(v1Input),v2(v2Input){
            i1 = 0;
            i2 = 0;
            n1 = v1.size()-1;
            n2 = v2.size()-1;
        }
        int next(){
            if(i1<=i2 || i2>n2) return v1[i1++];
            else return v2[i2++];
        }
        bool hasNext(){
            return !(i1>n1 && i2>n2);
        }
};

class RangeBaseIterator{
    private:
        int _start, _end, _stepValue, _currentValue;
    public:
        RangeBaseIterator(int start, int end, int stepValue){
            _start = start;
            _end = end;
            _stepValue = stepValue;
            _currentValue = 0;
        }
        int next(){
            if(_currentValue == 0)_currentValue = _start;
            else _currentValue+=_stepValue;
            return _currentValue;
        }
        bool hasNext(){
            return (_currentValue+_stepValue <= _end);
        }
};

int main() {
    cout<<"Interleaving Iterator"<<endl;
    vector<int> v1 = {1,2,3};
    vector<int> v2 = {4,5,6};
    InterLeavingIterator interLeavingIterator(v1,v2);
    while(interLeavingIterator.hasNext()){
        cout<<interLeavingIterator.next()<<endl;
    }
    
    cout<<"Range Iterator"<<endl;
    RangeBaseIterator rangeBaseIterator(2,20,3);
    while(rangeBaseIterator.hasNext()){
        cout<<rangeBaseIterator.next()<<endl;
    }
}

```