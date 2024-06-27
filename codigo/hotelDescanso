#include <iostream>
#include <string>
#include <fstream>
#include <sstream>
#include <iomanip>
#include <ctime>

class Hotel {
public:
    void EscolheOpcao(int& o) {
        std::cout << "Bem Vindo ao Hotel California. \nEscolha uma das opções para seguir com o seu atendimento:\n[1] Cliente\n[2] Funcionário\n[3] Estadia\n[4] Quarto\n[5] Checkout\n[0] Sair\n";
        std::cin >> o;
        switch (o) {
            case 1:
                Cliente(o);
                break;
            case 2:
                Funcionario(o);
                break;
            case 3:
                Estadia(o);
                break;
            case 4:
                Quarto(o);
                break;
            case 5:
                Checkout(o);
                break;
            case 0:
                Saida(o);
                break;
            default:
                std::cout << "Opção inválida\n";
        }
    }

    void Cliente(int& o) {
        std::cout << "Você escolheu a opção CADASTRO DE CLIENTE\n[1] - Cadastrar\n[2] - Visualizar\n[3] - Voltar\n";
        int acao;
        std::cin >> acao;
        if (acao == 1) {
            int codigo, telefone;
            std::string nome, endereco;
            std::cout << "Digite o codigo do cliente: ";
            std::cin >> codigo;

            if (codigoExiste("clientes.txt", codigo)) {
                std::cout << "Código de cliente já existe!\n";
            } else {
                std::cout << "Digite o nome do cliente: ";
                std::cin.ignore(); // Limpar o buffer
                std::getline(std::cin, nome);
                std::cout << "Digite o endereço do cliente: ";
                std::getline(std::cin, endereco);
                std::cout << "Digite o telefone do cliente (Apenas digitos): ";
                std::cin >> telefone;
                cadastraCliente("clientes.txt", codigo, nome, endereco, telefone);
                std::cout << "Cliente cadastrado com sucesso!\n";
            }
        } else if (acao == 2) {
            int codigo;
            std::cout << "Digite o codigo do cliente: ";
            std::cin >> codigo;
            visualizarCliente("clientes.txt", codigo);
        } else if (acao == 3) {
            EscolheOpcao(o);
        } else {
            std::cout << "Opção inválida!\n";
            Cliente(o); // Chamada recursiva para tratar entrada inválida
        }
    }

    void Funcionario(int& o) {
        std::cout << "Você escolheu a opção CADASTRO DE FUNCIONARIO\n[1] - Cadastrar\n[2] - Visualizar\n[3] - Voltar\n";
        int acao;
        std::cin >> acao;
        if (acao == 1) {
            int codigo, telefone, salario;
            std::string nome, cargo;
            std::cout << "Digite o codigo do funcionario: ";
            std::cin >> codigo;

            if (codigoExiste("funcionarios.txt", codigo)) {
                std::cout << "Código de funcionário já existe!\n";
            } else {
                std::cout << "Digite o nome do funcionário: ";
                std::cin.ignore(); // Limpar o buffer
                std::getline(std::cin, nome);
                std::cout << "Digite o telefone do funcionário: ";
                std::cin >> telefone;
                std::cin.ignore(); // Limpar o buffer
                std::cout << "Digite o cargo do funcionário: ";
                std::getline(std::cin, cargo);
                std::cout << "Digite o salario do funcionário: ";
                std::cin >> salario;
                std::cin.ignore(); // Limpar o buffer
                cadastraFuncionario("funcionarios.txt", codigo, nome, telefone, cargo, salario);
                std::cout << "Funcionário cadastrado com sucesso!\n";
            }
        } else if (acao == 2) {
            int codigo;
            std::cout << "Digite o codigo do funcionario: ";
            std::cin >> codigo;
            visualizarFuncionario("funcionarios.txt", codigo);
        } else if (acao == 3) {
            EscolheOpcao(o);
        } else {
            std::cout << "Opção inválida!\n";
            Funcionario(o); // Chamada recursiva para tratar entrada inválida
        }
    }

    void Estadia(int& o) {
        std::cout << "Você escolheu a opção CADASTRO DE ESTADIA\n[1] - Cadastrar\n[2] - Visualizar\n[3] - Voltar\n";
        int acao;
        std::cin >> acao;
        if (acao == 1) {
            int codigoCliente, numeroQuarto, numeroHospedes;
            std::string dataEntrada, dataSaida;
            std::cout << "Digite o código do cliente: ";
            std::cin >> codigoCliente;

            if (!codigoExiste("clientes.txt", codigoCliente)) {
                std::cout << "Cliente não encontrado!\n";
            } else {
                std::cout << "Digite o número do quarto: ";
                std::cin >> numeroQuarto;

                if (!codigoExiste("quartos.txt", numeroQuarto)) {
                    std::cout << "Quarto não encontrado!\n";
                } else {
                    std::cout << "Digite o número de hóspedes: ";
                    std::cin >> numeroHospedes;

                    std::cout << "Digite a data de entrada (dd/mm/aaaa): ";
                    std::cin >> dataEntrada;

                    std::cout << "Digite a data de saída (dd/mm/aaaa): ";
                    std::cin >> dataSaida;

                    if (quartoDisponivel("estadias.txt", numeroQuarto, dataEntrada, dataSaida)) {
                        cadastraEstadia("estadias.txt", codigoCliente, numeroQuarto, numeroHospedes, dataEntrada, dataSaida);
                        std::cout << "Estadia cadastrada com sucesso!\n";
                    } else {
                        std::cout << "O quarto já está ocupado nesse período!\n";
                    }
                }
            }
        } else if (acao == 2) {
            int codigoCliente;
            std::cout << "Digite o código do cliente: ";
            std::cin >> codigoCliente;
            visualizarEstadia("estadias.txt", codigoCliente);
        } else if (acao == 3) {
            EscolheOpcao(o);
        } else {
            std::cout << "Opção inválida!\n";
            Estadia(o); // Chamada recursiva para tratar entrada inválida
        }
    }

    void Quarto(int& o) {
        std::cout << "Você escolheu a opção CADASTRO DE QUARTO\n[1] - Cadastrar\n[2] - Visualizar\n[3] - Voltar\n";
        int acao;
        std::cin >> acao;
        if (acao == 1) {
            int numero, hospedes, diaria;
            std::cout << "Digite o número do quarto: ";
            std::cin >> numero;

            if (codigoExiste("quartos.txt", numero)) {
                std::cout << "Este número de quarto já existe!\n";
            } else {
                std::cout << "Digite o número total de hóspedes permitidos: ";
                std::cin >> hospedes;
                std::cout << "Digite o valor da diária: ";
                std::cin >> diaria;
                cadastraQuarto("quartos.txt", numero, hospedes, diaria);
                std::cout << "Quarto cadastrado com sucesso!\n";
            }
        } else if (acao == 2) {
            int numero;
            std::cout << "Digite o número do quarto: ";
            std::cin >> numero;
            visualizarQuarto("quartos.txt", numero);
        } else if (acao == 3) {
            EscolheOpcao(o);
        } else {
            std::cout << "Opção inválida!\n";
            Quarto(o); // Chamada recursiva para tratar entrada inválida
        }
    }

    void Checkout(int& o) {
        std::cout << "Digite o número do quarto para fazer checkout: ";
        int numeroQuarto;
        std::cin >> numeroQuarto;

        std::ifstream infile("estadias.txt");
        if (!infile.is_open()) {
            std::cerr << "Erro ao abrir o arquivo estadias.txt\n";
            return;
        }

        bool quartoEncontrado = false;
        bool quartoOcupado = false;
        std::string line;
        while (std::getline(infile, line)) {
            std::istringstream iss(line);
            std::string codCliStr, numQuartoStr, numHospStr, dataEntrada, dataSaida;
            if (std::getline(iss, codCliStr, '|') && std::getline(iss, numQuartoStr, '|') && 
                std::getline(iss, numHospStr, '|') && std::getline(iss, dataEntrada, '|') && std::getline(iss, dataSaida, '|')) {
                int numQuarto = std::stoi(numQuartoStr);
                if (numQuarto == numeroQuarto) {
                    quartoEncontrado = true;

                    int diaria = obterDiaria(numeroQuarto);
                    if (diaria < 0) {
                        std::cerr << "Erro ao obter a diária do quarto.\n";
                        return;
                    }

                    // Calcular a diferença de dias entre a data de entrada e a data de saída
                    struct tm tm_entrada = {};
                    struct tm tm_saida = {};
                    strptime(dataEntrada.c_str(), "%d/%m/%Y", &tm_entrada);
                    strptime(dataSaida.c_str(), "%d/%m/%Y", &tm_saida);

                    time_t t_entrada = mktime(&tm_entrada);
                    time_t t_saida = mktime(&tm_saida);

                    double diff = difftime(t_saida, t_entrada) / (60 * 60 * 24);
                    if (diff >= 0) {
                        double valorEstadia = diff * diaria;
                        std::cout << "Valor a ser cobrado pela estadia: " << valorEstadia << " reais.\n";
                    } else {
                        std::cout << "Erro nas datas fornecidas.\n";
                    }

                    quartoOcupado = true;
                    break;
                }
            }
        }

        if (!quartoEncontrado) {
            std::cout << "Quarto não encontrado.\n";
        } else if (!quartoOcupado) {
            std::cout << "Quarto não está ocupado.\n";
        }
    }

    void Saida(int& o) {
        std::cout << "Saindo do programa\n";
        o = 0;
    }

private:
    bool codigoExiste(const std::string& arquivo, int codigo) {
        std::ifstream infile(arquivo);
        if (!infile.is_open()) {
            std::cerr << "Erro ao abrir o arquivo " << arquivo << "\n";
            return false;
        }

        std::string line;
        while (std::getline(infile, line)) {
            std::istringstream iss(line);
            std::string codigoStr;
            if (std::getline(iss, codigoStr, '|')) {
                int codigoArquivo = std::stoi(codigoStr);
                if (codigoArquivo == codigo) {
                    infile.close();
                    return true;
                }
            }
        }

        infile.close();
        return false;
    }

    void cadastraCliente(const std::string& arquivo, int codigo, const std::string& nome, const std::string& endereco, int telefone) {
        std::ofstream outfile(arquivo, std::ios_base::app);
        if (!outfile.is_open()) {
            std::cerr << "Erro ao abrir o arquivo " << arquivo << "\n";
            return;
        }

        outfile << codigo << '|' << nome << '|' << endereco << '|' << telefone << '\n';
        outfile.close();
    }

    void visualizarCliente(const std::string& arquivo, int codigo) {
        std::ifstream infile(arquivo);
        if (!infile.is_open()) {
            std::cerr << "Erro ao abrir o arquivo " << arquivo << "\n";
            return;
        }

        std::string line;
        bool encontrado = false;
        while (std::getline(infile, line)) {
            std::istringstream iss(line);
            std::string codigoStr, nome, endereco, telefoneStr;
            if (std::getline(iss, codigoStr, '|') && std::stoi(codigoStr) == codigo &&
                std::getline(iss, nome, '|') &&
                std::getline(iss, endereco, '|') &&
                std::getline(iss, telefoneStr, '|')) {
                int telefone = std::stoi(telefoneStr);
                std::cout << "Código: " << codigo << " \nNome: " << nome << " \nEndereço: " << endereco << " \nTelefone: " << telefone << "\n";
                encontrado = true;
                break;
            }
        }

        if (!encontrado) {
            std::cout << "Cliente não encontrado.\n";
        }

        infile.close();
    }

    void cadastraFuncionario(const std::string& arquivo, int codigo, const std::string& nome, int telefone, const std::string& cargo, int salario) {
        std::ofstream outfile(arquivo, std::ios_base::app);
        if (!outfile.is_open()) {
            std::cerr << "Erro ao abrir o arquivo " << arquivo << "\n";
            return;
        }

        outfile << codigo << '|' << nome << '|' << telefone << '|' << cargo << '|' << salario << '\n';
        outfile.close();
    }

    void visualizarFuncionario(const std::string& arquivo, int codigo) {
        std::ifstream infile(arquivo);
        if (!infile.is_open()) {
            std::cerr << "Erro ao abrir o arquivo " << arquivo << "\n";
            return;
        }

        std::string line;
        bool encontrado = false;
        while (std::getline(infile, line)) {
            std::istringstream iss(line);
            std::string codigoStr, nome, cargo, telefoneStr, salarioStr;
            if (std::getline(iss, codigoStr, '|') && std::stoi(codigoStr) == codigo &&
                std::getline(iss, nome, '|') &&
                std::getline(iss, telefoneStr, '|') &&
                std::getline(iss, cargo, '|') &&
                std::getline(iss, salarioStr, '|')) {
                int telefone = std::stoi(telefoneStr);
                int salario = std::stoi(salarioStr);
                std::cout << "Código: " << codigo << " \nNome: " << nome << "\nTelefone: " << telefone << "\nCargo: " << cargo << "\nSalário: " << salario << "\n";
                encontrado = true;
                break;
            }
        }

        if (!encontrado) {
            std::cout << "Funcionário não encontrado.\n";
        }

        infile.close();
    }

    bool quartoDisponivel(const std::string& arquivo, int numeroQuarto, const std::string& dataEntrada, const std::string& dataSaida) {
        std::ifstream infile(arquivo);
        if (!infile.is_open()) {
            std::cerr << "Erro ao abrir o arquivo " << arquivo << "\n";
            return false;
        }

        std::string line;
        while (std::getline(infile, line)) {
            std::istringstream iss(line);
            std::string numQuartoStr, dataEntradaArquivo, dataSaidaArquivo;
            if (std::getline(iss, numQuartoStr, '|') && std::stoi(numQuartoStr) == numeroQuarto &&
                std::getline(iss, dataEntradaArquivo, '|') &&
                std::getline(iss, dataSaidaArquivo, '|')) {
                if (temIntersecaoDatas(dataEntrada, dataSaida, dataEntradaArquivo, dataSaidaArquivo)) {
                    infile.close();
                    return false; // Quarto ocupado no período fornecido
                }
            }
        }

        infile.close();
        return true;
    }

    bool temIntersecaoDatas(const std::string& dataEntrada1, const std::string& dataSaida1, const std::string& dataEntrada2, const std::string& dataSaida2) {
        struct tm tm_entrada1 = {}, tm_saida1 = {}, tm_entrada2 = {}, tm_saida2 = {};
        strptime(dataEntrada1.c_str(), "%d/%m/%Y", &tm_entrada1);
        strptime(dataSaida1.c_str(), "%d/%m/%Y", &tm_saida1);
        strptime(dataEntrada2.c_str(), "%d/%m/%Y", &tm_entrada2);
        strptime(dataSaida2.c_str(), "%d/%m/%Y", &tm_saida2);

        time_t t_entrada1 = mktime(&tm_entrada1);
        time_t t_saida1 = mktime(&tm_saida1);
        time_t t_entrada2 = mktime(&tm_entrada2);
        time_t t_saida2 = mktime(&tm_saida2);

        return (t_entrada1 < t_saida2 && t_saida1 > t_entrada2);
    }

    void cadastraEstadia(const std::string& arquivo, int codigoCliente, int numeroQuarto, int numeroHospedes, const std::string& dataEntrada, const std::string& dataSaida) {
        std::ofstream outfile(arquivo, std::ios_base::app);
        if (!outfile.is_open()) {
            std::cerr << "Erro ao abrir o arquivo " << arquivo << "\n";
            return;
        }

        outfile << codigoCliente << '|' << numeroQuarto << '|' << numeroHospedes << '|' << dataEntrada << '|' << dataSaida << '\n';
        outfile.close();
    }

    void visualizarEstadia(const std::string& arquivo, int codigoCliente) {
        std::ifstream infile(arquivo);
        if (!infile.is_open()) {
            std::cerr << "Erro ao abrir o arquivo " << arquivo << "\n";
            return;
        }

        std::string line;
        bool encontrado = false;
        while (std::getline(infile, line)) {
            std::istringstream iss(line);
            std::string codCliStr, numQuartoStr, numHospStr, dataEntrada, dataSaida;
            if (std::getline(iss, codCliStr, '|') && std::stoi(codCliStr) == codigoCliente &&
                std::getline(iss, numQuartoStr, '|') &&
                std::getline(iss, numHospStr, '|') &&
                std::getline(iss, dataEntrada, '|') &&
                std::getline(iss, dataSaida, '|')) {
                int numQuarto = std::stoi(numQuartoStr);
                int numHosp = std::stoi(numHospStr);
                std::cout << "Código Cliente: " << codigoCliente << ", Número Quarto: " << numQuarto << ", Número Hóspedes: " << numHosp << ", Data Entrada: " << dataEntrada << ", Data Saída: " << dataSaida << "\n";
                encontrado = true;
                break;
            }
        }

        if (!encontrado) {
            std::cout << "Estadia não encontrada para este cliente.\n";
        }

        infile.close();
    }

    void cadastraQuarto(const std::string& arquivo, int numero, int hospedes, int diaria) {
        std::ofstream outfile(arquivo, std::ios_base::app);
        if (!outfile.is_open()) {
            std::cerr << "Erro ao abrir o arquivo " << arquivo << "\n";
            return;
        }

        outfile << numero << '|' << hospedes << '|' << diaria << '\n';
        outfile.close();
    }

    void visualizarQuarto(const std::string& arquivo, int numero) {
        std::ifstream infile(arquivo);
        if (!infile.is_open()) {
            std::cerr << "Erro ao abrir o arquivo " << arquivo << "\n";
            return;
        }

        std::string line;
        bool encontrado = false;
        while (std::getline(infile, line)) {
            std::istringstream iss(line);
            std::string numeroStr, hospedesStr, diariaStr;
            if (std::getline(iss, numeroStr, '|') && std::stoi(numeroStr) == numero &&
                std::getline(iss, hospedesStr, '|') &&
                std::getline(iss, diariaStr, '|')) {
                int hospedes = std::stoi(hospedesStr);
                int diaria = std::stoi(diariaStr);
                std::cout << "Número Quarto: " << numero << ", Número Máximo de Hóspedes: " << hospedes << ", Valor Diária: " << diaria << "\n";
                encontrado = true;
                break;
            }
        }

        if (!encontrado) {
            std::cout << "Quarto não encontrado.\n";
        }

        infile.close();
    }

    int obterDiaria(int numeroQuarto) {
        std::ifstream infile("quartos.txt");
        if (!infile.is_open()) {
            std::cerr << "Erro ao abrir o arquivo quartos.txt\n";
            return -1;
        }

        std::string line;
        while (std::getline(infile, line)) {
            std::istringstream iss(line);
            std::string numQuartoStr, hospedesStr, diariaStr;
            if (std::getline(iss, numQuartoStr, '|') && std::stoi(numQuartoStr) == numeroQuarto &&
                std::getline(iss, hospedesStr, '|') &&
                std::getline(iss, diariaStr, '|')) {
                int diaria = std::stoi(diariaStr);
                infile.close();
                return diaria;
            }
        }

        infile.close();
        return -1;
    }
};

int main() {
    Hotel hotel;
    int opcao;

    do {
        hotel.EscolheOpcao(opcao);
    } while (opcao != 0);

    return 0;
}
