# Event-Gerenciament
# --- Sistema de Gerenciamento de Eventos Universitários ---

# Nosso "banco de dados". Cada evento é um dicionário
# que contém uma lista de inscritos.
eventos = []
proximo_id = 1 # Para garantir um ID único para cada evento

# --- FUNÇÕES DO SISTEMA ---

def cadastrar_evento():
    """Função para cadastrar um novo evento."""
    global proximo_id
    print("\n--- Cadastrar Novo Evento ---")
    nome = input("Nome do evento: ")
    data = input("Data do evento (ex: DD/MM/AAAA): ")
    descricao = input("Descrição do evento: ")
    
    while True:
        try:
            vagas_maximas = int(input("Número máximo de participantes: "))
            break
        except ValueError:
            print("Número de vagas inválido. Digite um número inteiro.")

    evento = {
        "id": proximo_id,
        "nome": nome,
        "data": data,
        "descricao": descricao,
        "vagas_maximas": vagas_maximas,
        "inscritos": [] # Lista para guardar o nome dos participantes
    }
    
    eventos.append(evento)
    proximo_id += 1
    print(f"Evento '{nome}' cadastrado com sucesso!")

def visualizar_eventos():
    """Função para exibir todos os eventos disponíveis."""
    print("\n--- Eventos Disponíveis ---")
    if not eventos:
        print("Nenhum evento cadastrado no momento.")
    else:
        # Loop 'for' para percorrer a lista de eventos
        for evento in eventos:
            vagas_restantes = evento['vagas_maximas'] - len(evento['inscritos'])
            print(f"ID: {evento['id']} | Nome: {evento['nome']} | Data: {evento['data']}")
            print(f"Descrição: {evento['descricao']}")
            print(f"Vagas restantes: {vagas_restantes}\n")

def inscrever_em_evento():
    """Função para inscrever um aluno em um evento."""
    print("\n--- Inscrição em Evento ---")
    try:
        id_evento = int(input("Digite o ID do evento para se inscrever: "))
    except ValueError:
        print("ID inválido.")
        return

    evento_encontrado = None
    for evento in eventos:
        if evento['id'] == id_evento:
            evento_encontrado = evento
            break

    if not evento_encontrado:
        print("Evento não encontrado.")
        return
        
    # Estrutura condicional 'if' para verificar o limite de vagas
    if len(evento_encontrado['inscritos']) < evento_encontrado['vagas_maximas']:
        nome_aluno = input("Digite seu nome completo: ")
        evento_encontrado['inscritos'].append(nome_aluno)
        print(f"Inscrição de '{nome_aluno}' no evento '{evento_encontrado['nome']}' realizada com sucesso!")
    else:
        print("Inscrição não realizada. O evento já atingiu o número máximo de participantes.")

def visualizar_inscricoes():
    """Função para o organizador ver os inscritos de um evento."""
    print("\n--- Visualizar Inscrições ---")
    try:
        id_evento = int(input("Digite o ID do evento para ver os inscritos: "))
    except ValueError:
        print("ID inválido.")
        return

    evento_encontrado = None
    for evento in eventos:
        if evento['id'] == id_evento:
            evento_encontrado = evento
            break
    
    if evento_encontrado:
        print(f"\n--- Inscritos no Evento: {evento_encontrado['nome']} ---")
        if not evento_encontrado['inscritos']:
            print("Nenhum participante inscrito neste evento.")
        else:
            # Loop 'for' para listar os nomes
            for nome in evento_encontrado['inscritos']:
                print(f"- {nome}")
    else:
        print("Evento não encontrado.")
        
# --- LOOP PRINCIPAL DO PROGRAMA ---

while True:
    print("\n--- MENU - GERENCIAMENTO DE EVENTOS ---")
    print("1. Cadastrar Evento (Coordenador)")
    print("2. Visualizar Eventos Disponíveis (Todos)")
    print("3. Inscrever-se em um Evento (Aluno)")
    print("4. Visualizar Inscritos de um Evento (Coordenador)")
    print("5. Sair")
    
    opcao = input("Escolha uma opção: ")
    
    if opcao == '1':
        cadastrar_evento()
    elif opcao == '2':
        visualizar_eventos()
    elif opcao == '3':
        inscrever_em_evento()
    elif opcao == '4':
        visualizar_inscricoes()
    elif opcao == '5':
        print("Saindo do sistema...")
        break
    else:
        print("Opção inválida. Tente novamente.")
