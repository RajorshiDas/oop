#include <iostream>
using namespace std;
class registeration;
class login;
class subject_choice;
class information;
class student
{
    friend class registeration;
    friend class login;
    friend class subject_choice;
    friend class information;
private:
    string name,id,password;
    string subjects[5];

};
class registeration
{  public:
    void register_student(student &sample)
    {   string ex_name,ex_id,ex_password;
       cout<<"Enter your name:";
       cin>>ex_name;
       cout<<"Enter your ID number:";
       cin>>ex_id;
       cout<<"Enter your password:";
       cin>>ex_password;
       sample.name=ex_name;
       sample.id=ex_id;
       sample.password=ex_password;
       cout<<"registration successful !"<<endl;
    }

};
class login
{
public:
    void conform(student &sample)
    {    string idno;
         string passw;
        cout<<"Enter your id:";
        cin>>idno;

        cout<<"Enter your password:";
        cin>>passw;
        if(idno==sample.id && passw==sample.password)
        {
            cout<<"Welcome to subject choice panel"<<endl;
            cout<<"-------------------------------------"<<endl;

        }
        else
        {
            cout<<"not found!"<<endl;
            exit(0);
        }

            }

};
class subject_choice
{
public:
    void choice(student &sample)
    {   int i;
        for(i=0;i<5;i++)
        {     cout<<i+1<<":";
            string sub;
            cin>>sub;
            sample.subjects[i]=sub;
        }
    }
};


class information
{  public:
    void show(student &sample)
    {    cout<<"----------------------"<<endl;
        cout<<"Name:"<<sample.name<<endl;
        cout<<"ID number:"<<sample.id<<endl;
        cout<<"subject choice list"<<endl;
        cout<<"--------------"<<endl;
        for(int i=0;i<5;i++)
        cout<<i+1<<":"<<sample.subjects[i]<<endl;
    }
};


int main()
{     cout<<"\t\tWelcome to Kuet Admission Panel"<<endl;
cout<<"\t\t-------------------------------"<<endl;
    cout<<"First register you to login:"<<endl;
    student sample;
    registeration r;
    r.register_student(sample);
cout<<"-----------------------------------"<<endl;
    cout<<"Login to your ID"<<endl;
    login l;
    l.conform(sample);
    cout<<"Give subject choice"<<endl;
    cout<<"Available subjects are : EEE CSE ME CE ARCI(Put your subjects in accending order)"<<endl;
    cout<<"------------------------------------------"<<endl;

    subject_choice m;
    m.choice(sample);
     cout<<"Subject choice conformed"<<endl;
    cout<<"show information"<<endl;

     information in;
    in.show(sample);

    cout<<"Wait for subject allocation"<<endl;
    return 0;
}
