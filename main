#include <algorithm>
#include <vector>
#include <iostream>
#include <string>
#include <set>

void strip(std::string& s, char x){
    s.erase(std::remove_if(s.begin(),
                           s.end(),
                           [&](auto c){return c==x;}),
            s.end());
}
std::string parse_email(std::string email) {
    std::string local;
    std::string domain;
    auto at = std::find(email.begin(), email.end(), '@');
    if (at != email.end()) {
        local = std::string(email.begin(), at);
        strip(local, '.');
        domain = std::string(at + 1, email.end());
    }
    auto ignore = std::find(local.begin(), local.end(), '+');
    if (ignore != local.end()) {
        local = std::string(local.begin(), ignore);
    }
    return std::string {local + '@' + domain};
}
int main() {
    std::set<std::string> parsed_emails;
    std::vector<std::string> emails{"A.B+.C.D@gmail.com", "norm@yahoo.com", "norm+1@yahoo.com",
                                    "AB@gmail.com"};
    for(const auto& email : emails) {
        parsed_emails.insert(parse_email(email));
    }
    std::cout << parsed_emails.size();
    return 0;
}
