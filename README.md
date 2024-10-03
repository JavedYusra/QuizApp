# DEP
import java.rmi.*;
import java.rmi.server.*;

interface MyRemoteInterface extends Remote {
    String sayHello() throws RemoteException;
}

class MyRemoteImpl extends UnicastRemoteObject implements MyRemoteInterface {
    public MyRemoteImpl() throws RemoteException {
        super();
    }

    public String sayHello() {
        return "Hello from the Server!";
    }
}

public class MyRMIApplication {
    public static void main(String[] args) {
        try {
            MyRemoteImpl obj = new MyRemoteImpl();
            Naming.rebind("rmi://localhost:5000/hello", obj);
            System.out.println("Server is ready...");
        } catch (Exception e) {
            System.out.println("Server error: " + e);
        }
    }
}

class MyRMIClient {
    public static void main(String[] args) {
        try {
            MyRemoteInterface stub = (MyRemoteInterface) Naming.lookup("rmi://localhost:5000/hello");
            System.out.println(stub.sayHello());
        } catch (Exception e) {
            System.out.println("Client error: " + e);
        }
    }
}
