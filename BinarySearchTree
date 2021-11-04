#include<iostream>
#include<string.h>
#include<bits/stdc++.h>
using namespace std;
struct ContactNode
{
    string name;
    string phone;
    ContactNode *left;
    ContactNode *right;
};
class contact
{
private:
    ContactNode *root;
    void addContact(ContactNode *&p,string name,string phone)
    {
        if(p==NULL)
        {
            p= new ContactNode;
            p->name = name;
            p->phone = phone;
            p->left = NULL;
            p->right = NULL;
            cout<<"\nContact added sucessfully."<<endl;
        }
        else if(phone < p->phone  || phone > p->phone)
        {
            if(name < p->name )
            {
                addContact(p->left,name,phone);

            }
            else
            {
                addContact(p->right,name,phone);

            }

        }
        else if (phone == p->phone)
        {
            cout<<"\n !!!This number already exists in the contactbook!!! ";
        }

    }

    void print(ContactNode *p)
    {
        if(p==NULL)
        {
            return ;
        }
        print(p->left);
        cout<<"\n"<<endl;
        cout<< p->name<<endl;
        cout<< p->phone<<endl;
        print(p->right);
    }

    bool findNode(ContactNode* node, string src)
    {
        if(node==NULL)
        {
            return false;
        }
        string Name = node->name;
        transform(Name.begin(), Name.end(), Name.begin(), ::toupper);
        transform(src.begin(), src.end(), src.begin(), ::toupper);
        size_t found = Name.find(src);
        bool isFound=false;
        if(found != string::npos)
        {
            cout<<endl;
            cout << node->name<<" \n"<<node->phone<<endl;
            isFound=true;
        }
        isFound = findNode(node->left, src) || isFound;
        isFound = findNode(node->right, src)|| isFound;
        return isFound;
    }

    bool findPhone(ContactNode *tree, string phone)
    {
        if(tree==NULL)
        {
            cout<<"No match found."<<endl;
            return false;

        }
        if(strstr(tree->phone.c_str(),phone.c_str()))
        {
            return true;
        }
        else if(phone < tree->phone)
        {
            return findPhone(tree->left,phone);
        }
        else if(phone > tree->phone)
        {
            return findPhone(tree->right,phone);
        }
    }

    string findMinNode(ContactNode *tree)
    {
        if(tree == NULL)
        {
            return NULL;
        }
        else if(tree->left == NULL)
        {
            return tree->name,tree->phone;
        }
        else
        {
            return findMinNode(tree->left);
        }
    }
    string findMaxNode(ContactNode *tree)
    {
        if(tree == NULL)
        {
            return NULL;
        }
        else if(tree->right == NULL)
        {
            return tree->name,tree->phone;
        }
        else
        {
            return findMaxNode(tree->right);
        }
    }


    void deleteByNumber(ContactNode *&tree,string phone)
    {
        if(tree == NULL)
        {
            return;
        }
        if(tree->phone == phone)
        {
            if(tree->left == NULL && tree->right == NULL)
            {
                delete tree;
                tree = NULL;
            }
            else if(tree->left != NULL)
            {
                string maxLeftNode = findMaxNode(tree->left);
                tree->phone = maxLeftNode;
                deleteByNumber(tree->left,maxLeftNode);
            }
            else
            {
                string minRightNode = findMinNode(tree->right);
                tree->phone = minRightNode;
                deleteByNumber(tree->right,minRightNode);
            }
        }
        else if(tree->phone < phone)
        {
            deleteByNumber(tree->right, phone);
        }
        else
        {
            deleteByNumber(tree->left, phone);
        }
    }

public:
    contact()
    {
        root = NULL;
    }
    void addContact(string name,string phone)
    {
        addContact(root,name,phone);
    }
    void print()
    {
        print(root);
    }
    bool findNode(string src)
    {
        return findNode(root,src);
    }
    bool findPhone( string phone)
    {
        return findPhone(root,phone);
    }
    void deleteByNumber(string phone)
    {
        deleteByNumber(root,phone);
    }
};

void upperCase(string &convert)
{
    for(unsigned int i=0; i<convert.length(); i++)
    {
        convert[i] = toupper(convert[i]);
    }
}

int main()
{
    int menuOpt;
    menuOpt=0;
    string name,phone,src,deleteNum;
    contact c;
    while(menuOpt!=5)
    {
        cout<<"---------------------------"<<endl;
        cout<<"1. Add new contact"<<endl;
        cout<<"2. Display all contacts"<<endl;
        cout<<"3. Search for a contact"<<endl;
        cout<<"4. Delete a contact "<<endl;
        cout<<"5. Exit"<<endl;
        cout<<endl;
        cout<<"Enter your choice (1-5): ";
        cin>>menuOpt;

        if(menuOpt==1)
        {
            cout<<endl;

            cout<<">> Add new contact"<<endl;
            cout<<"\nEnter name: ";
            cin.ignore();
            getline(cin,name);
            upperCase(name);
//            transform(name.begin(), name.end(), name.begin(), ::toupper); //function
            cout<<"Enter phone number: ";
            cin>>phone;
            c.addContact(name,phone);


            cout<<endl;
        }
        else if(menuOpt==2)
        {
            cout<<endl;

            cout<<">> Display all contacts";
            c.print();

            cout<<endl;
            cout<<endl;

        }
        else if(menuOpt==3)
        {

            cout<<endl;
            cout<<">> Search for a contact "<<endl;
            cout<<"\nEnter name:";
            cin.ignore();
            getline(cin,src);
            upperCase(src);
//             char cw;
//            cout<< count(src.begin(), src.end(),src[cw])+1 << " matches found";
            cout<<"match found"<<endl;
            if(c.findNode(src)!=true)
            {
                cout<<"No match found."<<endl;
            }
            cout<<endl;
        }
        else if(menuOpt==4)
        {
            cout<<endl;
            cout<<">> Delete a contact"<<endl;
            cout<<"Enter phone number:"<<endl;
            cin>>deleteNum;
            char confirmation;
            if(c.findPhone(deleteNum))
            {
                cout<<"Match found"<<endl;
                cout<<"\nDelete this contact?"<<endl;
                cout<<"\nEnter y for yes, n for no: y"<<endl;
                cin>>confirmation;
                if(confirmation='Y'||'y')
                {
                    c.deleteByNumber(deleteNum);
                    cout<<"Contact deleted sucessfully."<<endl;
                }
            }
            else{
                cout<<"No match found."<<endl;
            }

            cout<<endl;
        }
        else
        {
            cout<<endl;
            cout<<"Progam has exited. ";
            break;
        }
    }

}
