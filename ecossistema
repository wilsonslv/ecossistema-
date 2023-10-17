import java.util.ArrayList;
import java.util.List;
import java.util.Random;

class SerVivo {
    protected String nome;
    protected int idade;

    public SerVivo(String nome) {
        this.nome = nome;
        this.idade = 0;
    }

    public void envelhecer() {
        idade++;
    }

    public void apresentar() {
        System.out.println("Eu sou um ser vivo chamado " + nome + " com " + idade + " anos de idade.");
    }
}

class Animal extends SerVivo {
    protected String especie;
    protected List<SerVivo> presas;

    public Animal(String nome, String especie) {
        super(nome);
        this.especie = especie;
        this.presas = new ArrayList<>();
    }

    public void adicionarPresa(SerVivo presa) {
        presas.add(presa);
    }

    public void movimentar() {
        System.out.println(nome + " se move de forma genérica.");
    }

    public void comer() {
        if (!presas.isEmpty()) {
            Random rand = new Random();
            int index = rand.nextInt(presas.size());
            SerVivo presa = presas.get(index);
            System.out.println(nome + " comeu " + presa.nome + " (" + presa.getClass().getSimpleName() + ").");
            presas.remove(presa);
        } else {
            System.out.println(nome + " não encontrou nenhuma presa para comer.");
        }
    }

    public void reproduzir() {
        System.out.println(nome + " está se reproduzindo.");
    }
}

class Lobo extends Animal {
    public Lobo(String nome) {
        super(nome, "Lobo");
    }

    @Override
    public void movimentar() {
        System.out.println(nome + " se move como um lobo.");
    }
}

class Coelho extends Animal {
    public Coelho(String nome) {
        super(nome, "Coelho");
    }

    @Override
    public void movimentar() {
        System.out.println(nome + " se move como um coelho.");
    }
}

class Planta extends SerVivo {
    protected String tipo;
    protected List<Animal> polinizadores;

    public Planta(String nome, String tipo) {
        super(nome);
        this.tipo = tipo;
        this.polinizadores = new ArrayList<>();
    }

    public void adicionarPolinizador(Animal animal) {
        polinizadores.add(animal);
    }

    public void crescer() {
        System.out.println(nome + " é uma planta do tipo " + tipo + " e está crescendo.");
    }

    public void polinizar() {
        if (!polinizadores.isEmpty()) {
            Random rand = new Random();
            int index = rand.nextInt(polinizadores.size());
            Animal polinizador = polinizadores.get(index);
            System.out.println(polinizador.nome + " polinizou " + nome + " (" + nome + ").");
        } else {
            System.out.println(nome + " não foi polinizada, pois não há polinizadores por perto.");
        }
    }
}

class Mamifero extends Animal {
    public Mamifero(String nome, String especie) {
        super(nome, especie);
    }

    public void amamentar() {
        System.out.println(nome + " é um mamífero e está amamentando seus filhotes.");
    }
}

class Ave extends Animal {
    public Ave(String nome, String especie) {
        super(nome, especie);
    }

    public void voar() {
        System.out.println(nome + " é uma ave e pode voar.");
    }
}

class Arvore extends Planta {
    public Arvore(String nome, String tipo) {
        super(nome, tipo);
    }

    public void darFrutos() {
        System.out.println(nome + " é uma árvore e está dando frutos.");
    }
}

class Arbusto extends Planta {
    public Arbusto(String nome, String tipo) {
        super(nome, tipo);
    }

    public void florescer() {
        System.out.println(nome + " é um arbusto e está florescendo.");
    }
}

class EcossistemaController {
    private List<SerVivo> seresVivos;

    public EcossistemaController() {
        seresVivos = new ArrayList<>();
    }

    public void adicionarSerVivo(SerVivo serVivo) {
        seresVivos.add(serVivo);
    }

    public void simularAno() {
        System.out.println("---- Novo Ano no Ecossistema ----");
        for (SerVivo serVivo : seresVivos) {
            serVivo.envelhecer();
            serVivo.apresentar();
            if (serVivo instanceof Animal) {
                ((Animal) serVivo).movimentar();
                ((Animal) serVivo).comer();
                ((Animal) serVivo).reproduzir();
            } else if (serVivo instanceof Planta) {
                ((Planta) serVivo).crescer();
                ((Planta) serVivo).polinizar();
            }
        }
    }
}

public class EcossistemaFloresta {
    public static void main(String[] args) {
        EcossistemaController ecossistema = new EcossistemaController();

        Arvore carvalho = new Arvore("Carvalho", "Árvore de Folha Caduca");
        Arvore cerejeira = new Arvore("Cerejeira", "Cerejeira Japonesa");
        Lobo lobo = new Lobo("Lobo Selvagem");
        Coelho coelho = new Coelho("Coelhinho Fofo");
        Mamifero urso = new Mamifero("Urso Marrom", "Urso");
        Ave aguia = new Ave("Águia Dourada", "Águia");

        carvalho.adicionarPolinizador(lobo);
        cerejeira.adicionarPolinizador(lobo);
        lobo.adicionarPresa(coelho);

        ecossistema.adicionarSerVivo(carvalho);
        ecossistema.adicionarSerVivo(cerejeira);
        ecossistema.adicionarSerVivo(lobo);
        ecossistema.adicionarSerVivo(coelho);
        ecossistema.adicionarSerVivo(urso);
        ecossistema.adicionarSerVivo(aguia);

        for (int ano = 1; ano <= 10; ano++) {
            ecossistema.simularAno();
        }
    }
}