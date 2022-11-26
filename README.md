# e104_ddm_jokenpo_kotlin

# Tutorial JoKenPo (Papel, Tesoura ou Pedra)

## Recursos
Antes de começar, faça o download das imagens utilizadas no projeto neste [link](https://github.com/e104SysDev/jokenpo/tree/main/app/src/main/res/drawable-v24).

## Step 01 - Criar Projeto
Crie um novo projeto como de costume e lembre-se de escolher a linguagem `Java` e uma `Empty Activity`.

Após o projeto concluir o `build` e baixar as dependências `gradle`, podemos prosseguir.

Crie uma nova `Activity` com o identificador `JogoActivity`, lembre-se clieque com o borão diretito do mouse sobre a pasta `app` e selecione `New/Activity/Empty Activity`

## Step 02 - Incluir os recursos
Adicione as imagens já baixadas previamente e as copie para a pasta `res/drawable` no projeto Android.

## Step 03 - UI
Neste passo iremos criar a Inteface Gráfica do projeto; temos duas telas, a tela pricipal (activity_main) e a tela do jogo (activity_jogo).
O detalhamento da crição das telas estão demonstrados nos vídeos das aula 10 e 11, neste tutorial iremos focar na implementação, então logo abaixo serão listados os códigos completos dos arquivos que compõem a interface gráfica de cadas uma das telas.

### MainActivity
Copie o código abaixo para o arquivo `activity_main.xml`.
```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <ImageView
        android:id="@+id/imageView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="32dp"
        android:adjustViewBounds="true"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:srcCompat="@drawable/jokenpo" />

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="16dp"
        android:text="The Game"
        android:textAppearance="@style/TextAppearance.AppCompat.Display3"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/imageView" />

    <com.google.android.material.textfield.TextInputLayout
        android:id="@+id/textInputLayoutContainer"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="16dp"
        android:layout_marginTop="16dp"
        android:layout_marginEnd="16dp"
        android:hint="Digite o seu nome, jogador..."
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView">

        <com.google.android.material.textfield.TextInputEditText
            android:id="@+id/textInputLayoutNome"
            android:layout_width="match_parent"
            android:layout_height="wrap_content" />
    </com.google.android.material.textfield.TextInputLayout>

    <Button
        android:id="@+id/buttonPlay"
        android:layout_width="0dp"
        android:layout_height="60dp"
        android:layout_marginStart="16dp"
        android:layout_marginTop="16dp"
        android:layout_marginEnd="16dp"
        android:onClick="iniciarJogo"
        android:text="Jogar"
        app:cornerRadius="32dp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textInputLayoutContainer" />
</androidx.constraintlayout.widget.ConstraintLayout>

```

### JogoActivity
Copie o código abaixo para o arquivo `activity_jogo.xml`.

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <ImageView
        android:id="@+id/imageViewTesoura"
        android:layout_width="120dp"
        android:layout_height="120dp"
        android:onClick="jogar"
        app:layout_constraintEnd_toStartOf="@+id/imageViewPedra"
        app:layout_constraintStart_toEndOf="@+id/imageViewPapel"
        app:layout_constraintTop_toTopOf="@+id/imageViewPedra"
        app:srcCompat="@drawable/tesoura_png" />

    <ImageView
        android:id="@+id/imageViewPedra"
        android:layout_width="120dp"
        android:layout_height="120dp"
        android:layout_marginEnd="16dp"
        android:layout_marginBottom="16dp"
        android:onClick="jogar"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:srcCompat="@drawable/pedra_png" />

    <ImageView
        android:id="@+id/imageViewPapel"
        android:layout_width="120dp"
        android:layout_height="120dp"
        android:layout_marginStart="16dp"
        android:layout_marginBottom="16dp"
        android:onClick="jogar"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:srcCompat="@drawable/papel_png" />

    <ImageView
        android:id="@+id/imageViewJogador"
        android:layout_width="240dp"
        android:layout_height="240dp"
        android:adjustViewBounds="true"
        android:cropToPadding="false"
        android:scaleType="centerInside"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:srcCompat="@drawable/voce" />

    <ImageView
        android:id="@+id/imageViewComputador"
        android:layout_width="150dp"
        android:layout_height="150dp"
        android:layout_marginTop="16dp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:srcCompat="@drawable/computador_png" />

    <TextView
        android:id="@+id/textViewComputador"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Computador"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/imageViewComputador" />

    <TextView
        android:id="@+id/textViewStatusPartida"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Você"
        android:textSize="24sp"
        android:textStyle="bold"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/imageViewJogador" />

    <TextView
        android:id="@+id/textView4"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="16dp"
        android:text="Vitórias"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="@+id/imageViewComputador" />

    <TextView
        android:id="@+id/textViewPontosJogador"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="0"
        android:textSize="24sp"
        android:textStyle="bold"
        app:layout_constraintStart_toStartOf="@+id/textView4"
        app:layout_constraintTop_toBottomOf="@+id/textView4" />

    <TextView
        android:id="@+id/textView6"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="16dp"
        android:text="Derrotas"
        app:layout_constraintStart_toStartOf="@+id/textViewPontosJogador"
        app:layout_constraintTop_toBottomOf="@+id/textViewPontosJogador" />

    <TextView
        android:id="@+id/textViewPontosComputador"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="0"
        android:textSize="24sp"
        android:textStyle="bold"
        app:layout_constraintStart_toStartOf="@+id/textView6"
        app:layout_constraintTop_toBottomOf="@+id/textView6" />

    <Button
        android:id="@+id/button"
        style="@style/Widget.MaterialComponents.Button.OutlinedButton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginEnd="16dp"
        android:text="Sair"
        android:visibility="gone"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintTop_toTopOf="@+id/imageViewComputador" />

    <TextView
        android:id="@+id/textView2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="16dp"
        android:text="Empates"
        app:layout_constraintStart_toStartOf="@+id/textViewPontosComputador"
        app:layout_constraintTop_toBottomOf="@+id/textViewPontosComputador" />

    <TextView
        android:id="@+id/textViewEmpates"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="0"
        android:textSize="24sp"
        android:textStyle="bold"
        app:layout_constraintStart_toStartOf="@+id/textView2"
        app:layout_constraintTop_toBottomOf="@+id/textView2" />
</androidx.constraintlayout.widget.ConstraintLayout>
```
## Step 04 - Implementando as funcionalidades em Java
Nesta passo iremos implementar as funcionalidades das duas telas utilizando `Java`. 

### Tela Principal

Esta tela tem por objetivo capturar o nome do jogador e inicializar o Jogo.

Iremos capturar o nome do jogador e enviar o nome capturado para a tela do jogo, conforme as instruções abaixo na classe `MainActivity`:

1. Declare um objeto da classe TextInputLayout como global.
```java
TextInputLayout textInputLayout;
```
2. Inicilaize o objeto no método `onCreate()`;
```java
textInputLayout = findViewById(R.id.textInputLayoutContainer);
```
3. Crie a função `iniciarJogo(View view)`, esta função criará um objeto Intent, incluirá o nome do jogador e inicializará a tela de início do jogo.
```java
    public void iniciarJogo(View view) {
        String jogador = Objects.requireNonNull(textInputLayout.getEditText()).getText().toString();
        Intent intent = new Intent(getApplicationContext(), GameActivity.class);
        intent.putExtra("nomeJogador", jogador);
        startActivity(intent);
    }
```
4. Confira o código criado:
```kotlin
class MainActivity : AppCompatActivity() {
    var textInputLayout: TextInputLayout? = null
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        textInputLayout = findViewById(R.id.textInputLayoutContainer)
    }

    fun iniciarJogo(view: View?) {
        val jogador = Objects.requireNonNull(textInputLayout!!.editText).text.toString()
        val intent = Intent(applicationContext, GameActivity::class.java)
        intent.putExtra("nomeJogador", jogador)
        startActivity(intent)
    }
}
```

### Tela do Jogo

Neste passo iremos implementar a lógica aplicada para as interações e processamentos realizados no App.

1. Declare os objetos globais na classe `JogoActivity`.
```java
    var mapImages: Map<Int, Int>? = null
    var opcoesComputador: List<Int>? = null
    var IdsOpcoesComputador: MutableList<Int?>? = null
    var mPapel: ImageView? = null
    var mTesoura: ImageView? = null
    var mPedra: ImageView? = null
    var mComputador: ImageView? = null
    var mJogador: ImageView? = null
    var placarJogador: Int = 0
    var placarComputador:Int = 0
    var empate:Int = 0

    var mPontosJogador: TextView? = null
    var mPontosComputador:TextView? = null
    var mStatusPartida:TextView? = null
    var mPontosEmpate:TextView? = null
    var status = ""
    var random = Random()

```
2. Crie a função para receber o nome do jogador através do método getIntent() e inclua sua chamada no método `onCreate`.
```kotlin
    @RequiresApi(api = Build.VERSION_CODES.N)
    private fun alterarTituloAppBar() {
        val nomeJogador = intent.getStringExtra("nomeJogador")
        if (Objects.nonNull(nomeJogador) && Boolean.FALSE == nomeJogador!!.isEmpty()) {
            this.title = "$nomeJogador jogando"
        }
    }
```
3. Crie uma função para configurar os ImageViews criados e faça uma chamada à este método no `onCreate`.
```kotlin
    private fun configurarImageViews() {
        opcoesComputador =
            Arrays.asList(R.drawable.papel_png, R.drawable.tesoura_png, R.drawable.pedra_png)
        IdsOpcoesComputador =
            Arrays.asList(R.id.imageViewPapel, R.id.imageViewTesoura, R.id.imageViewPedra)
        mapImages = HashMap()
        (mapImages as HashMap<Int, Int>).put(R.id.imageViewPapel, R.drawable.papel_png)
        (mapImages as HashMap<Int, Int>).put(R.id.imageViewTesoura, R.drawable.tesoura_png)
        (mapImages as HashMap<Int, Int>).put(R.id.imageViewPedra, R.drawable.pedra_png)
        (mapImages as HashMap<Int, Int>).put(R.id.imageViewComputador, R.drawable.computador_png)
        (mapImages as HashMap<Int, Int>).put(R.id.imageViewJogador, R.drawable.voce)
        mPapel = findViewById(R.id.imageViewPapel)
        mTesoura = findViewById(R.id.imageViewTesoura)
        mPedra = findViewById(R.id.imageViewPedra)
        mComputador = findViewById(R.id.imageViewComputador)
        mJogador = findViewById(R.id.imageViewJogador)
    }
```

4. Crie uma função para configurar os TextViews criados e faça uma chamada à este método no `onCreate`.
```kotlin
    private fun configurarTextViews() {
        mPontosJogador = findViewById<TextView>(R.id.textViewPontosJogador)
        mPontosComputador = findViewById<TextView>(R.id.textViewPontosComputador)
        mStatusPartida = findViewById<TextView>(R.id.textViewStatusPartida)
        mPontosEmpate = findViewById<TextView>(R.id.textViewEmpates)
    }
```
5. Verifique as chamadas no `onCreate`.
```kotlin
    @RequiresApi(Build.VERSION_CODES.N)
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_jo_ken_po)

        alterarTituloAppBar()
        configurarImageViews()
        configurarTextViews()
    }
```

#### Implementado a Lógica
Neste ponto, todos os recurso visuais estão configurados e organizados; agora podemos iniciar a `Lógica` do jogo.

1. Crie os Enums `Jogada` e `Status` pra facilitar a manipulação de constantes e a legibilidade, eles serão declarados no nível das funções, verifique a identação do código.
```kotlin
internal enum class Status(val status: String) {
        GANHOU("GANHOU"), PERDEU("PERDEU"), EMPATOU("EMPATOU");

    }

    internal enum class Jogada(val id: Int) {
        PAPEL(R.id.imageViewPapel), TESOURA(R.id.imageViewTesoura), PEDRA(R.id.imageViewPedra);

        companion object {
            fun toEnum(id: Int): Jogada {
                for (jogada in Jogada.values()) {
                    if (jogada.id == id) return jogada
                }
                throw RuntimeException("Id inválido: $id")
            }
        }
    }
```

2. Crie o método que realiza a jogada do computador, o computador irá sortear um número aleatório entre 0 e 2 e cada um destes valores representará `[Papel, Tesoura, Pedras]`, respectivamente. Esta função realizar a trocas das imagens com base no número aleatório e logo após ela devolve o id o objeto que disparou a função para que possamos reutilizar o retorno com a identificação da jogada realizada.
Adicione o método abaixo:
```kotlin
    fun jogadaComputador(): Int? {
        val valorRandomico: Int = random.nextInt(3)
        val idResource: Int? = opcoesComputador?.get(valorRandomico)
        if (idResource != null) {
            mComputador?.setImageResource(idResource)
        }
        return IdsOpcoesComputador?.get(valorRandomico)
    }
```

Neste ponto, sempre que tocar nas imagens Papel, Tesoura ou Pedra a imagem do usuário será alterada, mas a iagem do computador ainda não.
Precisamos crair uma função que execute a jogada do usuário e a jogada do computador, ambas retornam as escolhas realizadas. Precisamos capturar estas escolhas e criar a lógica parav definir o vencedor.

3. Crie a função que realiza as jogadas do usuário e do computador com base na imagem selecionada.
```kotlin
private fun definirVendedor(jogadaUsuario: Jogada, jogadaComputador: Jogada?) {
        when (jogadaUsuario) {
            Jogada.PAPEL -> if (Jogada.PEDRA == jogadaComputador) {
                placarJogador++
                status = Status.GANHOU.status
            } else if (Jogada.TESOURA == jogadaComputador) {
                placarComputador++
                status = Status.PERDEU.status
            } else {
                empate++
                status = Status.EMPATOU.status
            }
            Jogada.TESOURA -> if (Jogada.PAPEL == jogadaComputador) {
                placarJogador++
                status = Status.GANHOU.status
            } else if (Jogada.PEDRA == jogadaComputador) {
                placarComputador++
                status = Status.PERDEU.status
            } else {
                empate++
                status = Status.EMPATOU.status
            }
            Jogada.PEDRA -> if (Jogada.TESOURA == jogadaComputador) {
                placarJogador++
                status = Status.GANHOU.status
            } else if (Jogada.PAPEL == jogadaComputador) {
                placarComputador++
                status = Status.PERDEU.status
            } else {
                empate++
                status = Status.EMPATOU.status
            }
        }
        atualizaPlacar()
    }
```

4. Adicione o método que atualiza os dados.
```java
    private void atualizaPlacar() {
        mPontosComputador.setText(String.valueOf(placarComputador));
        mPontosJogador.setText(String.valueOf(placarJogador));
        mPontosEmpate.setText(String.valueOf(empate));
        mStatusPartida.setText(status);
    }
```

5. Finalizando o Jogo:
Agora precisamos que uma função realize a jogada do usuário, a jogada do computador, obtenha os valores das jogadas e chame a função que definirá o vencedor.
```kotlin
    private fun atualizaPlacar() {
        mPontosComputador?.setText(placarComputador.toString())
        mPontosJogador?.setText(placarJogador.toString())
        mPontosEmpate?.setText(empate.toString())
        mStatusPartida?.setText(status)
    }
```
6. Toque final. Adicione a chamada da função `atualizarPlacar` na função `definirVencedor`para atualizar os pontos a cada jogada. Adicione-o à penúltima linha do método `definirVencedor`.

#### Confira o código completo teste o App.
```kotlin
class JoKenPoActivity : AppCompatActivity() {

    var mapImages: Map<Int, Int>? = null
    var opcoesComputador: List<Int>? = null
    var IdsOpcoesComputador: MutableList<Int?>? = null
    var mPapel: ImageView? = null
    var mTesoura: ImageView? = null
    var mPedra: ImageView? = null
    var mComputador: ImageView? = null
    var mJogador: ImageView? = null
    var placarJogador: Int = 0
    var placarComputador:Int = 0
    var empate:Int = 0

    var mPontosJogador: TextView? = null
    var mPontosComputador:TextView? = null
    var mStatusPartida:TextView? = null
    var mPontosEmpate:TextView? = null
    var status = ""
    var random = Random()

    @RequiresApi(Build.VERSION_CODES.N)
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_jo_ken_po)

        alterarTituloAppBar()
        configurarImageViews()
        configurarTextViews()
    }

    @RequiresApi(api = Build.VERSION_CODES.N)
    private fun alterarTituloAppBar() {
        val nomeJogador = intent.getStringExtra("nomeJogador")
        if (Objects.nonNull(nomeJogador) && Boolean.FALSE == nomeJogador!!.isEmpty()) {
            this.title = "$nomeJogador jogando"
        }
    }

    private fun configurarTextViews() {
        mPontosJogador = findViewById<TextView>(R.id.textViewPontosJogador)
        mPontosComputador = findViewById<TextView>(R.id.textViewPontosComputador)
        mStatusPartida = findViewById<TextView>(R.id.textViewStatusPartida)
        mPontosEmpate = findViewById<TextView>(R.id.textViewEmpates)
    }

    fun jogar(v: View) {
        val jogador = Jogada.toEnum(jogadaUsuario(v))
        val computador = jogadaComputador()?.let { Jogada.toEnum(it) }
        definirVendedor(jogador, computador)
    }

    private fun definirVendedor(jogadaUsuario: Jogada, jogadaComputador: Jogada?) {
        when (jogadaUsuario) {
            Jogada.PAPEL -> if (Jogada.PEDRA == jogadaComputador) {
                placarJogador++
                status = Status.GANHOU.status
            } else if (Jogada.TESOURA == jogadaComputador) {
                placarComputador++
                status = Status.PERDEU.status
            } else {
                empate++
                status = Status.EMPATOU.status
            }
            Jogada.TESOURA -> if (Jogada.PAPEL == jogadaComputador) {
                placarJogador++
                status = Status.GANHOU.status
            } else if (Jogada.PEDRA == jogadaComputador) {
                placarComputador++
                status = Status.PERDEU.status
            } else {
                empate++
                status = Status.EMPATOU.status
            }
            Jogada.PEDRA -> if (Jogada.TESOURA == jogadaComputador) {
                placarJogador++
                status = Status.GANHOU.status
            } else if (Jogada.PAPEL == jogadaComputador) {
                placarComputador++
                status = Status.PERDEU.status
            } else {
                empate++
                status = Status.EMPATOU.status
            }
        }
        atualizaPlacar()
    }

    private fun atualizaPlacar() {
        mPontosComputador?.setText(placarComputador.toString())
        mPontosJogador?.setText(placarJogador.toString())
        mPontosEmpate?.setText(empate.toString())
        mStatusPartida?.setText(status)
    }

    private fun jogadaUsuario(v: View): Int {
        val idResource = v.id
        mJogador?.setImageResource(Objects.requireNonNull<Int>(mapImages?.get(idResource)))
        return idResource
    }

    fun jogadaComputador(): Int? {
        val valorRandomico: Int = random.nextInt(3)
        val idResource: Int? = opcoesComputador?.get(valorRandomico)
        if (idResource != null) {
            mComputador?.setImageResource(idResource)
        }
        return IdsOpcoesComputador?.get(valorRandomico)
    }

    private fun configurarImageViews() {
        opcoesComputador =
            Arrays.asList(R.drawable.papel_png, R.drawable.tesoura_png, R.drawable.pedra_png)
        IdsOpcoesComputador =
            Arrays.asList(R.id.imageViewPapel, R.id.imageViewTesoura, R.id.imageViewPedra)
        mapImages = HashMap()
        (mapImages as HashMap<Int, Int>).put(R.id.imageViewPapel, R.drawable.papel_png)
        (mapImages as HashMap<Int, Int>).put(R.id.imageViewTesoura, R.drawable.tesoura_png)
        (mapImages as HashMap<Int, Int>).put(R.id.imageViewPedra, R.drawable.pedra_png)
        (mapImages as HashMap<Int, Int>).put(R.id.imageViewComputador, R.drawable.computador_png)
        (mapImages as HashMap<Int, Int>).put(R.id.imageViewJogador, R.drawable.voce)
        mPapel = findViewById(R.id.imageViewPapel)
        mTesoura = findViewById(R.id.imageViewTesoura)
        mPedra = findViewById(R.id.imageViewPedra)
        mComputador = findViewById(R.id.imageViewComputador)
        mJogador = findViewById(R.id.imageViewJogador)
    }

    internal enum class Status(val status: String) {
        GANHOU("GANHOU"), PERDEU("PERDEU"), EMPATOU("EMPATOU");

    }

    internal enum class Jogada(val id: Int) {
        PAPEL(R.id.imageViewPapel), TESOURA(R.id.imageViewTesoura), PEDRA(R.id.imageViewPedra);

        companion object {
            fun toEnum(id: Int): Jogada {
                for (jogada in Jogada.values()) {
                    if (jogada.id == id) return jogada
                }
                throw RuntimeException("Id inválido: $id")
            }
        }
    }
}
```

# DIVIRTA-SE
