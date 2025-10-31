#include <iostream>
#include <string>
using namespace std;

int passwordStrength(string pass) {
    int score = 0;
    if (pass.length() >= 8) score++;
    bool hasUpper = false, hasLower = false, hasDigit = false, hasSymbol = false;
    for (char c : pass) {
        if (isupper(c)) hasUpper = true;
        else if (islower(c)) hasLower = true;
        else if (isdigit(c)) hasDigit = true;
        else hasSymbol = true;
    }
    if (hasUpper && hasLower) score++;
    if (hasDigit) score++;
    if (hasSymbol) score++;
    return score;
}

int main() {
    string password;
    cout << "Enter password: ";
    cin >> password;
    int strength = passwordStrength(password);
    cout << "Password strength: " << strength << "/4" << endl;
}
