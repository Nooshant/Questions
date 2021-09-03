```
import java.util.concurrent.locks.ReentrantLock;
import java.util.concurrent.locks.ReentrantReadWriteLock;
import java.util.concurrent.locks.ReentrantReadWriteLock.ReadLock;
import java.util.concurrent.locks.ReentrantReadWriteLock.WriteLock;

public class Shared {
	
	ReentrantReadWriteLock readWriteLock = new ReentrantReadWriteLock();
	public void m1() {
		//readWriteLock.lock()
		ReadLock lock = readWriteLock.readLock();
		lock.lock();
		//
		
			WriteLock lock1 = readWriteLock.writeLock();
			lock1.lock();
		    //
			lock1.unlock();
			
		lock.unlock();
		
	}
	
	public void m2() {
		
	}
	
   public synchronized void m3() {
		
	}
   
   public static synchronized void m4() {
		
  	}
   
   // shared -> obj
   // t1, t2
   //t1-> s.m1()
   //t2 -> s.m3()
   //  t2 Shared.m4()

}

```
