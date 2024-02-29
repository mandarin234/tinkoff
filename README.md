# tinkoff
import UIKit

class ViewController: UIViewController {
    
    // Экран калькулятора для отображения ввода и результата
    let display = UILabel()
    
    override func viewDidLoad() {
        super.viewDidLoad()
        setupCalculatorInterface()
    }
    
    func setupCalculatorInterface() {
        // Настройка экрана калькулятора
        display.textAlignment = .right
        display.backgroundColor = .lightGray
        display.text = "0"
        view.addSubview(display)
        
        // Настройка кнопок калькулятора
        let buttonTitles = [
            "C", "/", "*", "-", 
            "7", "8", "9", "+", 
            "4", "5", "6", "=", 
            "1", "2", "3", "", 
            "0", ".", ""
        ]
        
        let buttons = buttonTitles.map { title -> UIButton in
            let button = UIButton(type: .system)
            button.setTitle(title, for: .normal)
            button.addTarget(self, action: #selector(buttonTapped(_:)), for: .touchUpInside)
            return button
        }
        
        // Создание сетки кнопок
        let grid = UIStackView(arrangedSubviews: buttons)
        grid.axis = .vertical
        grid.distribution = .fillEqually
        grid.alignment = .fill
        grid.spacing = 1
        
        // Добавление сетки кнопок на экран
        view.addSubview(grid)
        
        // Констрейнты для экрана и сетки кнопок
        // ...
    }
    
    @objc func buttonTapped(_ sender: UIButton) {
        guard let title = sender.title(for: .normal) else { return }
        
        switch title {
        case "C":
            // Очистка экрана
            display.text = "0"
        case "/", "*", "-", "+", "=":
            // Обработка арифметических операций
            // ...
        default:
            // Добавление цифр на экран
            if display.text == "0" {
                display.text = title
            } else {
                display.text?.append(title)
            }
        }
    }
}
