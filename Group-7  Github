1. Date Class with Overloaded Operators
#include <iostream>
using namespace std;

class Date {
private:
    int day, month, year;

    bool isLeapYear(int y) {
        return (y % 4 == 0 && y % 100 != 0) || (y % 400 == 0);
    }

    int daysInMonth(int m, int y) {
        if (m == 2) return isLeapYear(y) ? 29 : 28;
        if (m == 4 || m == 6 || m == 9 || m == 11) return 30;
        return 31;
    }

public:
    Date(int d = 1, int m = 1, int y = 2000) : day(d), month(m), year(y) {}

    // Overload relational operators
    bool operator<(const Date& other) const {
        if (year != other.year) return year < other.year;
        if (month != other.month) return month < other.month;
        return day < other.day;
    }

    bool operator<=(const Date& other) const {
        return *this < other || *this == other;
    }

    bool operator>(const Date& other) const {
        return !(*this <= other);
    }

    bool operator>=(const Date& other) const {
        return !(*this < other);
    }

    bool operator==(const Date& other) const {
        return day == other.day && month == other.month && year == other.year;
    }

    bool operator!=(const Date& other) const {
        return !(*this == other);
    }

    // Overload ++ operator to increment date by one day
    Date& operator++() {
        day++;
        if (day > daysInMonth(month, year)) {
            day = 1;
            month++;
            if (month > 12) {
                month = 1;
                year++;
            }
        }
        return *this;
    }

    // Overload + operator to add given number of days
    Date operator+(int days) const {
        Date newDate = *this;
        while (days > 0) {
            newDate++;
            days--;
        }
        return newDate;
    }

    // Conversion to int (days elapsed in the current year)
    operator int() const {
        int daysElapsed = day;
        for (int m = 1; m < month; m++) {
            daysElapsed += daysInMonth(m, year);
        }
        return daysElapsed;
    }

    void display() const {
        cout << day << "/" << month << "/" << year << endl;
    }
};

int main() {
    Date dt(28, 2, 2024);
    ++dt;
    dt.display(); // Should display 29/2/2024

    Date dt2 = dt + 3;
    dt2.display(); // Should display 3/3/2024

    int daysElapsed = dt;
    cout << "Days elapsed in the current year: " << daysElapsed << endl;

    return 0;
}

2. Sorting Books by Author Name
#include <iostream>
#include <fstream>
#include <vector>
#include <algorithm>
using namespace std;

struct Book {
    int book_id;
    string author_name;
    double price;
    int no_of_pages;
    string publisher;
    int year_of_publishing;
};

bool compareByAuthor(const Book& a, const Book& b) {
    return a.author_name < b.author_name;
}

int main() {
    ifstream infile("books.txt");
    ofstream outfile("sorted_books.txt");
    vector<Book> books;
    Book book;

    while (infile >> book.book_id >> book.author_name >> book.price >> book.no_of_pages >> book.publisher >> book.year_of_publishing) {
        books.push_back(book);
    }

    sort(books.begin(), books.end(), compareByAuthor);

    for (const auto& b : books) {
        outfile << b.book_id << " " << b.author_name << " " << b.price << " " << b.no_of_pages << " " << b.publisher << " " << b.year_of_publishing << endl;
    }

    infile.close();
    outfile.close();

    return 0;
}

3. Vector Class Template
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

template <typename T>
class Vector {
private:
    vector<T> elements;

public:
    void addElement(T element) {
        elements.push_back(element);
    }

    T findSmallest() {
        return *min_element(elements.begin(), elements.end());
    }

    bool searchElement(T element) {
        return find(elements.begin(), elements.end(), element) != elements.end();
    }

    double findAverage() {
        T sum = accumulate(elements.begin(), elements.end(), T(0));
        return static_cast<double>(sum) / elements.size();
    }
};

int main() {
    Vector<int> vec;
    vec.addElement(10);
    vec.addElement(20);
    vec.addElement(5);
    vec.addElement(15);

    cout << "Smallest element: " << vec.findSmallest() << endl;
    cout << "Element 20 found: " << (vec.searchElement(20) ? "Yes" : "No") << endl;
    cout << "Average of elements: " << vec.findAverage() << endl;

    return 0;
}

4. Generic Function to Find the Largest of Three Numbers
#include <iostream>
using namespace std;

template <typename T>
T findLargest(T a, T b, T c) {
    return max(a, max(b, c));
}

int main() {
    cout << "Largest of 3, 5, 2: " << findLargest(3, 5, 2) << endl;
    cout << "Largest of 7.5, 3.2, 5.8: " << findLargest(7.5, 3.2, 5.8) << endl;
    cout << "Largest of 'a', 'z', 'm': " << findLargest('a', 'z', 'm') << endl;

    return 0;
}
