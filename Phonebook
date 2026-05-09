import java.util.Scanner;

public class Phonebook {

    // ── Node for BST ──────────────────────────────────────────
    static class BSTNode {
        String personName;
        String phoneNumber;
        BSTNode left, right;

        BSTNode(String name, String phone) {
            personName = name;
            phoneNumber = phone;
            left = null;
            right = null;
        }
    }

    // ── Node for Doubly Linked List ───────────────────────────
    static class DLLNode {
        String personName;
        String phoneNumber;
        DLLNode prev, next;

        DLLNode(String name, String phone) {
            personName = name;
            phoneNumber = phone;
            prev = null;
            next = null;
        }
    }

    // ══════════════════════════════════════════════════════════
    //   BST METHODS
    // ══════════════════════════════════════════════════════════

    static BSTNode bstRoot = null;

    static BSTNode bstInsert(BSTNode root, String name, String phone) {
        if (root == null)
            return new BSTNode(name, phone);
        if (name.compareToIgnoreCase(root.personName) < 0)
            root.left = bstInsert(root.left, name, phone);
        else if (name.compareToIgnoreCase(root.personName) > 0)
            root.right = bstInsert(root.right, name, phone);
        else {
            System.out.println("Contact already exists. Phone updated.");
            root.phoneNumber = phone;
        }
        return root;
    }

    static BSTNode bstSearch(BSTNode root, String name) {
        if (root == null) return null;
        if (name.equalsIgnoreCase(root.personName)) return root;
        if (name.compareToIgnoreCase(root.personName) < 0)
            return bstSearch(root.left, name);
        else
            return bstSearch(root.right, name);
    }

    static BSTNode bstFindMin(BSTNode root) {
        while (root.left != null) root = root.left;
        return root;
    }

    static BSTNode bstRemove(BSTNode root, String name) {
        if (root == null) return null;
        if (name.compareToIgnoreCase(root.personName) < 0)
            root.left = bstRemove(root.left, name);
        else if (name.compareToIgnoreCase(root.personName) > 0)
            root.right = bstRemove(root.right, name);
        else {
            if (root.left == null) return root.right;
            if (root.right == null) return root.left;
            BSTNode succ = bstFindMin(root.right);
            root.personName = succ.personName;
            root.phoneNumber = succ.phoneNumber;
            root.right = bstRemove(root.right, succ.personName);
        }
        return root;
    }

    static void bstUpdate(BSTNode root, String name, String newPhone) {
        BSTNode node = bstSearch(root, name);
        if (node != null) {
            node.phoneNumber = newPhone;
            System.out.println("Phone updated successfully.");
        } else {
            System.out.println("Contact not found.");
        }
    }

    static void bstDisplay(BSTNode root) {
        if (root == null) return;
        bstDisplay(root.left);
        System.out.println("  Name: " + root.personName + "  |  Phone: " + root.phoneNumber);
        bstDisplay(root.right);
    }

    static void bstIsolate0100(BSTNode root) {
        if (root == null) return;
        bstIsolate0100(root.left);
        if (root.phoneNumber.startsWith("0100"))
            System.out.println("  Name: " + root.personName + "  |  Phone: " + root.phoneNumber);
        bstIsolate0100(root.right);
    }

    static int bstSize(BSTNode root) {
        if (root == null) return 0;
        return 1 + bstSize(root.left) + bstSize(root.right);
    }

    // ══════════════════════════════════════════════════════════
    //   DOUBLY LINKED LIST METHODS
    // ══════════════════════════════════════════════════════════

    static DLLNode dllHead = null;

    static void dllInsert(String name, String phone) {
        DLLNode newNode = new DLLNode(name, phone);

        if (dllHead == null) {
            dllHead = newNode;
            return;
        }

        DLLNode curr = dllHead;
        while (curr != null) {
            int cmp = name.compareToIgnoreCase(curr.personName);
            if (cmp == 0) {
                System.out.println("Contact already exists. Phone updated.");
                curr.phoneNumber = phone;
                return;
            }
            if (cmp < 0) break;
            curr = curr.next;
        }

        if (curr == dllHead) {
            newNode.next = dllHead;
            dllHead.prev = newNode;
            dllHead = newNode;
        } else if (curr == null) {
            DLLNode temp = dllHead;
            while (temp.next != null) temp = temp.next;
            temp.next = newNode;
            newNode.prev = temp;
        } else {
            newNode.prev = curr.prev;
            newNode.next = curr;
            curr.prev.next = newNode;
            curr.prev = newNode;
        }
    }

    static DLLNode dllSearch(String name) {
        DLLNode curr = dllHead;
        while (curr != null) {
            if (name.equalsIgnoreCase(curr.personName)) return curr;
            curr = curr.next;
        }
        return null;
    }

    static void dllRemove(String name) {
        DLLNode curr = dllHead;
        while (curr != null) {
            if (name.equalsIgnoreCase(curr.personName)) {
                if (curr.prev != null) curr.prev.next = curr.next;
                else dllHead = curr.next;
                if (curr.next != null) curr.next.prev = curr.prev;
                System.out.println("Contact removed.");
                return;
            }
            curr = curr.next;
        }
        System.out.println("Contact not found.");
    }

    static void dllUpdate(String name, String newPhone) {
        DLLNode node = dllSearch(name);
        if (node != null) {
            node.phoneNumber = newPhone;
            System.out.println("Phone updated successfully.");
        } else {
            System.out.println("Contact not found.");
        }
    }

    static void dllDisplay() {
        if (dllHead == null) { System.out.println("Phonebook is empty."); return; }
        DLLNode curr = dllHead;
        while (curr != null) {
            System.out.println("  Name: " + curr.personName + "  |  Phone: " + curr.phoneNumber);
            curr = curr.next;
        }
    }

    static void dllIsolate0100() {
        DLLNode curr = dllHead;
        boolean found = false;
        while (curr != null) {
            if (curr.phoneNumber.startsWith("0100")) {
                System.out.println("  Name: " + curr.personName + "  |  Phone: " + curr.phoneNumber);
                found = true;
            }
            curr = curr.next;
        }
        if (!found) System.out.println("No contacts starting with 0100.");
    }

    static int dllSize() {
        int count = 0;
        DLLNode curr = dllHead;
        while (curr != null) { count++; curr = curr.next; }
        return count;
    }

    // ══════════════════════════════════════════════════════════
    //   MAIN MENU
    // ══════════════════════════════════════════════════════════

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // pre-load sample data
        bstRoot = bstInsert(bstRoot, "Ahmed Hassan", "01119876543");
        bstRoot = bstInsert(bstRoot, "Zara Ali",     "01001234567");
        bstRoot = bstInsert(bstRoot, "Mona Samir",   "01001112233");
        bstRoot = bstInsert(bstRoot, "Bassem Nour",  "01234567890");
        bstRoot = bstInsert(bstRoot, "Layla Omar",   "01001005500");
        bstRoot = bstInsert(bstRoot, "Omar Sherif",  "01100203040");
        bstRoot = bstInsert(bstRoot, "Rania Tarek",  "01001999888");

        dllInsert("Ahmed Hassan", "01119876543");
        dllInsert("Zara Ali",     "01001234567");
        dllInsert("Mona Samir",   "01001112233");
        dllInsert("Bassem Nour",  "01234567890");
        dllInsert("Layla Omar",   "01001005500");
        dllInsert("Omar Sherif",  "01100203040");
        dllInsert("Rania Tarek",  "01001999888");

        int choice;
        do {
            System.out.println("\n========== PHONEBOOK MENU ==========");
            System.out.println("1. Insert contact");
            System.out.println("2. Search contact");
            System.out.println("3. Remove contact");
            System.out.println("4. Update phone number");
            System.out.println("5. Display all contacts (A to Z)");
            System.out.println("6. Isolate contacts starting with 0100");
            System.out.println("7. Show size");
            System.out.println("0. Exit");
            System.out.println("=====================================");
            System.out.print("Enter choice: ");
            choice = sc.nextInt();
            sc.nextLine();

            switch (choice) {
                case 1:
                    System.out.print("Enter name  : ");
                    String iName = sc.nextLine();
                    System.out.print("Enter phone : ");
                    String iPhone = sc.nextLine();
                    if (iName.isEmpty() || iPhone.isEmpty()) {
                        System.out.println("Error: name and phone cannot be empty.");
                        break;
                    }
                    bstRoot = bstInsert(bstRoot, iName, iPhone);
                    dllInsert(iName, iPhone);
                    System.out.println("Contact inserted.");
                    break;

                case 2:
                    System.out.print("Enter name to search: ");
                    String sName = sc.nextLine();
                    System.out.println("-- BST Result --");
                    BSTNode br = bstSearch(bstRoot, sName);
                    System.out.println(br != null ? "Found -> " + br.personName + " | " + br.phoneNumber : "Not found.");
                    System.out.println("-- DLL Result --");
                    DLLNode dr = dllSearch(sName);
                    System.out.println(dr != null ? "Found -> " + dr.personName + " | " + dr.phoneNumber : "Not found.");
                    break;

                case 3:
                    System.out.print("Enter name to remove: ");
                    String rName = sc.nextLine();
                    System.out.println("-- BST --");
                    bstRoot = bstRemove(bstRoot, rName);
                    System.out.println("Removed.");
                    System.out.println("-- DLL --");
                    dllRemove(rName);
                    break;

                case 4:
                    System.out.print("Enter name to update : ");
                    String uName = sc.nextLine();
                    System.out.print("Enter new phone      : ");
                    String uPhone = sc.nextLine();
                    System.out.println("-- BST --");
                    bstUpdate(bstRoot, uName, uPhone);
                    System.out.println("-- DLL --");
                    dllUpdate(uName, uPhone);
                    break;

                case 5:
                    System.out.println("-- BST Display (A to Z) --");
                    if (bstRoot == null) System.out.println("Phonebook is empty.");
                    else bstDisplay(bstRoot);
                    System.out.println("-- DLL Display (A to Z) --");
                    dllDisplay();
                    break;

                case 6:
                    System.out.println("-- BST: Contacts starting with 0100 --");
                    bstIsolate0100(bstRoot);
                    System.out.println("-- DLL: Contacts starting with 0100 --");
                    dllIsolate0100();
                    break;

                case 7:
                    System.out.println("BST size = " + bstSize(bstRoot));
                    System.out.println("DLL size = " + dllSize());
                    break;

                case 0:
                    System.out.println("Goodbye!");
                    break;

                default:
                    System.out.println("Invalid choice. Try again.");
            }
        } while (choice != 0);

        sc.close();
    }
}
