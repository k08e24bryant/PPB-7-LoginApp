



## Cara Setup
1. Buka Android Studio
2. Buat project baru pilih "Empty Activity"
3. Kasih nama `LoginApp`
4. Pilih bahasa Kotlin
5. Centang "Use Jetpack Compose"

## File Penting

### 1. MainActivity.kt
```kotlin
@Composable
fun LoginScreen() {
    var email by remember { mutableStateOf("") }
    var password by remember { mutableStateOf("") }

    Column(
        modifier = Modifier.padding(24.dp),
        verticalArrangement = Arrangement.Center
    ) {
        // Gambar ilustrasi
        Image(
            painter = painterResource(R.drawable.login_illustration),
            contentDescription = null,
            modifier = Modifier.height(150.dp)
        
        // Judul
        Text("Welcome Back", style = MaterialTheme.typography.headlineMedium)
        Text("Login to your account", color = Color.Gray)

        // Input email
        OutlinedTextField(
            value = email,
            onValueChange = { email = it },
            label = { Text("Email") },
            modifier = Modifier.fillMaxWidth()
        )

        // Input password
        OutlinedTextField(
            value = password,
            onValueChange = { password = it },
            label = { Text("Password") },
            visualTransformation = PasswordVisualTransformation(),
            modifier = Modifier.fillMaxWidth()
        )

        // Tombol login
        Button(
            onClick = { /* logic login */ },
            modifier = Modifier.fillMaxWidth()
        ) {
            Text("LOGIN")
        }

        // Lupa password
        Text("Lupa password?", color = Color.Blue)

        // Pembatas
        Row(verticalAlignment = Alignment.CenterVertically) {
            Divider(Modifier.weight(1f))
            Text("ATAU", modifier = Modifier.padding(horizontal = 8.dp))
            Divider(Modifier.weight(1f))
        }

        // Tombol sosial media
        Row(horizontalArrangement = Arrangement.spacedBy(16.dp)) {
            IconButton(onClick = { /* facebook */ }) {
                Icon(painterResource(R.drawable.facebook_logo), null)
            }
            IconButton(onClick = { /* google */ }) {
                Icon(painterResource(R.drawable.google_logo), null)
            }
        }
    }
}
```

### 2. Theme.kt
```kotlin
private val DarkColorScheme = darkColorScheme(
    primary = Purple80,
    secondary = PurpleGrey80
)

@Composable
fun LoginAppTheme(
    darkTheme: Boolean = isSystemInDarkTheme(),
    content: @Composable () -> Unit
) {
    val colors = if (darkTheme) DarkColorScheme else LightColorScheme
    
    MaterialTheme(
        colorScheme = colors,
        content = content
    )
}
```

## Cara Pakai
1. Taruh gambar di folder `res/drawable`:
   - `login_illustration.png`
   - `facebook_logo.png`
   - `google_logo.png`


## Fitur
- Input email & password
- Tombol login
- Login dengan Facebook/Google
- Tampilan responsive


