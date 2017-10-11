ArrayList
===========================

All Implemented Interfaces:
Serializable, Cloneable, Iterable<E>, Collection<E>, List<E>, RandomAccess
Direct Known Subclasses:
AttributeList, RoleList, RoleUnresolvedLis

# Constructors
ArrayList()
Constructs an empty list with an initial capacity of ten.
ArrayList(Collection<? extends E> c)
Constructs a list containing the elements of the specified collection, in the order they are returned by the collection's iterator.
ArrayList(int initialCapacity)
Constructs an empty list with the specified initial capacity.
List arrayList = new ArrayList();
When the size is larger than 10, will relocate a larger memory. 
10->16->25->38->58->88->...
Every time you add a value that would increase the size beyond capacity a new array is created whose capacity is one more than 150% the previous capacity with the contents of the previous array copied within.
public void ensureCapacity(int minCapacity) 
{  
    modCount++;  
    int oldCapacity = elementData.length;  
    if (minCapacity > oldCapacity) 
    {  
        Object oldData[] = elementData;  
        int newCapacity = (oldCapacity * 3)/2 + 1;  
            if (newCapacity < minCapacity)  
        newCapacity = minCapacity;  
            // minCapacity is usually close to size, so this is a win:  
            elementData = Arrays.copyOf(elementData, newCapacity);  
    }  
}  

ArrayList can contain "any number of items" (Integer.MAX) and when doing large initial insertions you can tell ArrayList to allocate a larger storage to begin with as to not waste CPU cycles when it tries to allocate more space for the next item.

Reference:https://docs.oracle.com/javase/7/docs/api/java/util/ArrayList.html
