#include <iostream>
using namespace std;

int main()
{
    cout << "Please enter expression (we can handle +, -, *, and /)\n";
    cout << "add an x to end expression (e.g., 1+2*3x): ";
    int lval = 0;
    int rval = 0;

    if (!(cin >> lval)) {
        cerr << "no first operand\n";
        return 1;
    }

    for (char op; cin >> op; ) {
        if (op == 'x') {                                 // terminate and print result
            cout << "Result: " << lval << '\n';
            return 0;
        }

        if (!(cin >> rval)) {
            cerr << "no second operand\n";
            return 1;
        }

        switch (op) {
            case '+': lval += rval; break;
            case '-': lval -= rval; break;
            case '*': lval *= rval; break;
            case '/':
                if (rval == 0) {
                    cerr << "division by zero\n";
                    return 1;
                }
                lval /= rval;
                break;
            default:
                cerr << "bad operator: " << op << '\n';
                return 1;
        }
    }

    cerr << "bad expression\n";
    return 1;
}
