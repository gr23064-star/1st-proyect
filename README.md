import random
import time
import sys

def portada():
    print("\n" + "#"*60)
    print("#" + " "*58 + "#")
    print("#" + " "*12 + "🔥 GRAN CONCURSO DE COMIDA VALENCIANA 🔥" + " "*10 + "#")
    print("#" + " "*58 + "#")
    print("#" + " "*12 + "¿Serás el auténtico Chef Valenciano del año?" + " "*7 + "#")
    print("#" + " "*58 + "#")
    print("#" + " "*9 + "➤ Descubre, acierta y suma puntos 🌟" + " "*15 + "#")
    print("#" + " "*9 + "➤ ¡Premio a quien más sepa de platos valencianos!" + " "*7 + "#")
    print("#"*60 + "\n")
    print("Reglas: Se mostrarán platos típicos. Acierta el ingrediente principal. Si fallas, restas puntos. ¡A por la paella de oro!")
    input("\nPulsa Enter para empezar el concurso...")

platos = [
    {
        "plato": "Paella Valenciana",
        "pregunta": "¿Cuál es uno de sus ingredientes principales?",
        "options": ["Conejo", "Chorizo", "Mariscos", "Pimentón"],
        "answer": 0
    },
    {
        "plato": "Fideuà",
        "pregunta": "¿Qué ingrediente no puede faltar en una fideuà?",
        "options": ["Fideos", "Arroz", "Pan", "Garbanzos"],
        "answer": 0
    },
    {
        "plato": "Horchata",
        "pregunta": "¿De qué se elabora la auténtica horchata valenciana?",
        "options": ["Chufa", "Almendra", "Coco", "Avellana"],
        "answer": 0
    },
    {
        "plato": "Buñuelos de calabaza",
        "pregunta": "¿Qué verdura lleva este dulce típico de Fallas?",
        "options": ["Calabaza", "Berenjena", "Zanahoria", "Patata"],
        "answer": 0
    },
    {
        "plato": "Turrón de Jijona",
        "pregunta": "¿Cuál es su ingrediente fundamental?",
        "options": ["Almendra", "Harina", "Queso", "Nuez"],
        "answer": 0
    },
    {
        "plato": "Arroz al horno",
        "pregunta": "¿Qué embutido se le suele añadir?",
        "options": ["Morcilla", "Chorizo", "Salchichón", "Jamón"],
        "answer": 0
    },
    {
        "plato": "Tortilla de patatas con cebolla",
        "pregunta": "¿Cuál es el ingrediente estrella además del huevo?",
        "options": ["Patata", "Chufa", "Maíz", "Calabacín"],
        "answer": 0
    },
]

def efectos_visuals(acierto):
    anim = "👏" if acierto else "❌"
    for i in range(3):
        print(anim, end=" ", flush=True)
        time.sleep(0.3)
    print("\n")

def juego():
    puntos = 0
    random.shuffle(platos)
    for idx, q in enumerate(platos, 1):
        print(f"\nROUND {idx}/{len(platos)} → {q['plato'].upper()}")
        print(q['pregunta'])
        for opt_idx, opt in enumerate(q['options']):
            print(f"  {opt_idx+1}. {opt}")
        user = input("Elige opción (número): ")
        if user.isdigit() and int(user)-1 == q['answer']:
            efectos_visuals(True)
            print("¡Correcto! Sumas +3 puntos\n")
            puntos += 3
        else:
            efectos_visuals(False)
            print(f"¡Incorrecto! Restas -2 puntos. Respuesta: '{q['options'][q['answer']]}'\n")
            puntos -= 2
        time.sleep(1)
        print(f"PUNTOS TOTALES: {puntos}")
        time.sleep(0.3)
    print("\n" + "*"*40)
    if puntos >= 15:
        print("🎉 ¡Enhorabuena, eres Maestro/a de la Cocina Valenciana! 🎉")
    elif puntos >= 0:
        print("¡Buen intento! Sigue aprendiendo y disfruta los sabores valencianos.")
    else:
        print("¡Ánimo! Te toca probar más platos y practicar.")
    print(f"Puntuación final: {puntos} puntos")
    print("*"*40)

if __name__ == "__main__":
    portada()
    juego()
