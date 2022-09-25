# PARAMETROS ARGC PARA EXECUCAO DO CODIGO (SE NECESSÁRIO)

# ARQUIVO DE ENTRADA
ENTRADAS = 
# ARQUIVO DE SAÌDA
SAIDA = 

# ARQUIVO GABARITO, SE TIVER
SAIDA_ESPERADA = 

# nome do arquivo executável
EXECUTAVEL = executavel.exe

# nome do compilador
CPP = gcc

# opções de compilação
CFLAGS = -Wall -g -lm

# opções do valgrind
VFLAGS = -s --leak-check=full

# define lista de arquivos-fonte.
FONTES = $(wildcard SRC/*.c)

# define lista de arquivos-headers.
HEADERS = $(wildcard HEADERS/*.h)

# define lista dos arquivos-objeto usando nomes da lista de arquivos-fonte
OBJ_FOLDER = OBJ
OBJETOS = $(subst SRC,$(OBJ_FOLDER),$(FONTES:.c=.o))

############ ALVOS

# gera o executável, a pasta obj e armazena os .o nela
all: $(OBJ_FOLDER) $(EXECUTAVEL)

# gera pasta dos arquivos-objetos
$(OBJ_FOLDER):
	@mkdir -p $@

# linka o executável aos arquivos-objeto
$(EXECUTAVEL): $(OBJETOS)
	@$(CPP) -o $@ $^ $(CFLAGS)

# gera arquivos-objeto
$(OBJ_FOLDER)/%.o: SRC/%.c
	@$(CPP) -c $(CFLAGS) $< -o $@

# comando para executar, deve especificar sempre os arquivos de entrada e saida.
run:
	@./$(EXECUTAVEL) $(ENTRADAS) $(SAIDA)

# comando para limpeza.
clean:
	@rm -rf $(OBJ_FOLDER) $(EXECUTAVEL)

# Comando para comparar a saída feita com a saída esperada
dif:
	diff $(SAIDA) $(SAIDA_ESPERADA)

# comando para analise da memoria.
val:
	@valgrind $(VFLAGS) ./$(EXECUTAVEL) $(ENTRADAS) $(SAIDA)
