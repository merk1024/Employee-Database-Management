---

# Система учёта персонала

Этот проект был создан с образовательной целью для демонстрации работы с JavaFX, интеграции с MySQL и реализации базовых операций (Создание, Чтение, Обновление, Удаление) в системе управления сотрудниками.

---

## Технологии
- **Язык программирования:** [Java 1.8.0_202](https://drive.google.com/file/d/1QerZhUeBnsGpoHyO77nfpUHhLI-kqeYe/view?usp=sharing)
- **Графический интерфейс:** JavaFX
- **База данных:** [MySQL](https://sourceforge.net/projects/xampp/files/XAMPP%20Windows/8.0.30/xampp-windows-x64-8.0.30-0-VS16-installer.exe)
- **Среда разработки:** [NetBeans 8.0](https://drive.google.com/file/d/19FqkmSH_GBqrPnXZ4sudnT-x2DlX0tbb/view?usp=sharing)
- **Дополнительные инструменты:** [Scene Builder](https://drive.google.com/file/d/13Uh-Feaiz-PgzXTFW_EU0sxurS4tnNzQ/view?usp=sharing)

---

## Основные возможности
1. **Авторизация:** Защищённый вход для администраторов и пользователей.
2. **Управление сотрудниками:** Возможность добавления, редактирования и удаления данных о сотрудниках, включая их имя, пол, должность, отдел, зарплату и контактную информацию.
3. **Работа с отделами и должностями:** Создание и управление записями отделов и должностей для сотрудников.
4. **Интеграция с базой данных:** Используется MySQL для хранения и обработки данных.
5. **Современный интерфейс:** Приложение разработано с использованием JavaFX для интуитивно понятного взаимодействия.

---

## Установка
1. Клонируйте репозиторий на локальный компьютер.
2. Импортируйте проект в NetBeans.
3. Настройте параметры подключения к MySQL (пользователь — `root`, пароль — `1234`).
4. Запустите проект.

---

## Настройка базы данных

### Команды для создания структуры:
```sql
CREATE DATABASE staff_management;
USE staff_management;

CREATE TABLE admin (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) NOT NULL,
    password VARCHAR(50) NOT NULL,
    role ENUM('Admin', 'User') DEFAULT 'User'
);

CREATE TABLE department (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL
);

CREATE TABLE designation (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL
);

CREATE TABLE employee (
    id INT AUTO_INCREMENT PRIMARY KEY,
    employee_id INT UNIQUE NOT NULL,
    name VARCHAR(100) NOT NULL,
    gender ENUM('Male', 'Female', 'Other') NOT NULL,
    department_id INT,
    designation_id INT,
    salary DECIMAL(10, 2),
    phone_number VARCHAR(20),
    epf_number VARCHAR(100),
    FOREIGN KEY (department_id) REFERENCES department(id),
    FOREIGN KEY (designation_id) REFERENCES designation(id)
);
```

### Добавление тестовых данных:
```sql
INSERT INTO admin (username, password, role) VALUES ('admin', '1234', 'Admin');
INSERT INTO department (name) VALUES ('HR'), ('IT'), ('Finance');
INSERT INTO designation (name) VALUES ('Manager'), ('Engineer'), ('Analyst');
```

---

## Скриншоты интерфейса
### Вход в систему
![image](https://github.com/K4viyamato/employee-management-system/assets/113100464/a46c0f8e-525e-40c6-8dc5-b09a3b1020bb)

### Панель управления
![image](https://github.com/K4viyamato/employee-management-system/assets/113100464/3ed52d9b-bc80-42b6-b0b9-1b3d5ba7e829)

---
