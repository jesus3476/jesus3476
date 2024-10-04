#include <Controllino.h>

void setup() {
    // Configura las entradas  
    pinMode(CONTROLLINO_D, INPUT); // Entrada A  
    pinMode(CONTROLLINO_D1, INPUT); // Entrada B  
    pinMode(CONTROLLINO_D2, INPUT); // Entrada C

    // Configura la salida para el LED  
    pinMode(CONTROLLINO_D3, OUTPUT); // LED  
}

void loop() {
    // Lee las entradas  
    bool A = digitalRead(CONTROLLINO_D); // Lee entrada A  
    bool B = digitalRead(CONTROLLINO_D1); // Lee entrada B  
    bool C = digitalRead(CONTROLLINO_D2); // Lee entrada C

    // Calcula las salidas de las puertas AND  
    bool AND1 = A && B; // Salida de la primera puerta AND  
    bool AND2 = AND1 && C; // Salida de la segunda puerta AND

    // Calcula la salida de la puerta OR  
    bool OR = AND2 || C; // Salida de la puerta OR

    // Controla el LED basado en la salida de la puerta OR  
    if (OR) {
        digitalWrite(CONTROLLINO_D3, HIGH); // Enciende el LED  
    } else {
        digitalWrite(CONTROLLINO_D3, LOW); // Apaga el LED  
    }

    delay(100); // Pequeña pausa para evitar lecturas rápidas  
}
