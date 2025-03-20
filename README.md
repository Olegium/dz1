# dz1
#include <QTextEdit>
#include <QApplication>
#include <QWidget>
#include <QVBoxLayout>
#include <QLabel>
#include <QLineEdit>
#include <QPushButton>

class Widget: public QWidget{
public:
    Widget() {
        QVBoxLayout *layout = new QVBoxLayout(this);// создали стол

        QLabel *label = new QLabel("Введите директорию ниже:");//создали текст
        layout->addWidget(label);

        QLineEdit *lineEdit = new QLineEdit(this);//создали окно ввода
        layout->addWidget(lineEdit);

        QPushButton *button = new QPushButton("Отправить", this);//кнопка
        layout->addWidget(button);

        QLabel *outputLabel = new QLabel("Введите фразу ниже:");
        layout->addWidget(outputLabel);

        QLineEdit *lineEdit2 = new QLineEdit(this);//создали окно ввода
        layout->addWidget(lineEdit2);

        QPushButton *button2 = new QPushButton("Отправить", this);//кнопка
        layout->addWidget(button2);

        QLabel *outputLabel2 = new QLabel("количества файлов");
        layout->addWidget(outputLabel2);

        QLabel *outputLabel3 = new QLabel("файл");

        connect(button2, &QPushButton::clicked, [lineEdit2, outputLabel2](){

        QString text = lineEdit2->text(); // Получаем текст из QLineEdit
        outputLabel2->setText("Количество файлов: " + text); // Выводим текст
        });

        setWindowTitle("Пример Qt Widgets");// окно настройка
        resize(300, 200);
        QTextEdit *textEdit = new QTextEdit(this);
                textEdit->setReadOnly(true); // Запрещаем редактирование
                layout->addWidget(textEdit);

        connect(button2, &QPushButton::clicked, [textEdit]() {
                    // 5 строковых переменных
                    QString line1 = "1 файл найденный";
                    QString line2 = "2 файл найденный";
                    QString line3 = "3 файл найденный";
                    QString line4 = "4 файл найденный";
                    QString line5 = "5 файл найденный";

                    // Объединяем строки с переносами
                    QString text = line1 + "\n" + line2 + "\n" + line3 + "\n" + line4 + "\n" + line5;

                    textEdit->setText(text);
                });
    }
};

int main(int argc, char *argv[])
{
    QApplication app(argc, argv);
    Widget widget;
    widget.show();
    return app.exec();
}
