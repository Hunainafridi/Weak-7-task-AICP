#include <iostream>
#include <vector>
#include <algorithm>
#include <numeric>

std::vector<std::string> setup_donation_system() {
    std::vector<std::string> charities;
    for (int i = 0; i < 3; ++i) {
        std::string charity_name;
        std::cout << "Enter name of charity " << i + 1 << ": ";
        std::cin >> charity_name;
        charities.push_back(charity_name);
    }
    return charities;
}

void record_and_total_donation(std::vector<std::string>& charities, std::vector<double>& charity_totals) {
    while (true) {
        try {
            std::cout << "\nCharities:\n";
            for (size_t i = 0; i < charities.size(); ++i) {
                std::cout << i + 1 << ". " << charities[i] << "\n";
            }
            std::cout << "Enter charity choice (1-3, or -1 to show totals): ";
            int charity_choice;
            std::cin >> charity_choice;

            if (charity_choice == -1) {
                break;
            }

            if (1 <= charity_choice && charity_choice <= 3) {
                std::cout << "Enter value of customer's shopping bill: ";
                double shopping_bill;
                std::cin >> shopping_bill;

                double donation = shopping_bill * 0.01;
                charity_totals[charity_choice - 1] += donation;

                std::cout << "Donation of $" << donation << " made to " << charities[charity_choice - 1] << "\n";
            } else {
                std::cout << "Invalid charity choice. Please enter 1, 2, 3, or -1.\n";
            }
        } catch (...) {
            std::cout << "Invalid input. Please enter numbers only.\n";
        }
    }
}

void show_totals(const std::vector<std::string>& charities, const std::vector<double>& charity_totals) {
    std::vector<std::pair<std::string, double>> sorted_totals(charities.size());
    for (size_t i = 0; i < charities.size(); ++i) {
        sorted_totals[i] = std::make_pair(charities[i], charity_totals[i]);
    }

    std::sort(sorted_totals.begin(), sorted_totals.end(),
              [](const auto& x, const auto& y) { return x.second > y.second; });

    double grand_total = std::accumulate(charity_totals.begin(), charity_totals.end(), 0.0);

    std::cout << "\nTotal donations so far:\n";
    for (const auto& [charity, total] : sorted_totals) {
        std::cout << charity << ": $" << total << "\n";
    }

    std::cout << "\nGRAND TOTAL DONATED TO CHARITY: $" << grand_total << "\n";
}

int main() {
    std::vector<std::string> charities = setup_donation_system();
    std::vector<double> charity_totals(charities.size(), 0.0);  // Initialize totals for each charity
    record_and_total_donation(charities, charity_totals);
    show_totals(charities, charity_totals);

    return 0;
}
