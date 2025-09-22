class Pagina:
    def __init__(self, titulo, url):
        self.titulo = titulo
        self.url = url
    
    def __str__(self):
        return f"{self.titulo} - {self.url}"

class Nodo:
    def __init__(self, pagina):
        self.pagina = pagina
        self.anterior = None
        self.siguiente = None

class Historial:
    def __init__(self):
        self.actual = None  # Nodo actual
        self.tamaño = 0
    
    def visitar(self, titulo, url):
        """Visita una nueva página. Si hay páginas adelante, las elimina."""
        nueva_pagina = Pagina(titulo, url)
        nuevo_nodo = Nodo(nueva_pagina)
        
        if self.actual is None:
            # Primera página
            self.actual = nuevo_nodo
        else:
            # Eliminar páginas hacia adelante (como un navegador)
            self.actual.siguiente = None
            
            # Conectar nueva página
            nuevo_nodo.anterior = self.actual
            self.actual.siguiente = nuevo_nodo
            self.actual = nuevo_nodo
        
        self.tamaño += 1
        print(f" Visitaste: {nueva_pagina}")
    
    def atras(self):
        """Retrocede una página en el historial."""
        if self.actual and self.actual.anterior:
            self.actual = self.actual.anterior
            print(f" Volviste a: {self.actual.pagina}")
            return self.actual.pagina
        else:
            print("No hay páginas atrás")
            return None
    
    def adelante(self):
        """Avanza una página en el historial."""
        if self.actual and self.actual.siguiente:
            self.actual = self.actual.siguiente
            print(f"→ Adelantaste a: {self.actual.pagina}")
            return self.actual.pagina
        else:
            print("No hay páginas adelante")
            return None
    
    def mostrar_historial(self):
        """Muestra todo el historial."""
        if self.actual is None:
            print("El historial está vacío")
            return
        
        # Encontrar el primer nodo
        primer_nodo = self.actual
        while primer_nodo.anterior:
            primer_nodo = primer_nodo.anterior
        
        # Mostrar desde el principio
        print("\n Historial completo:")
        nodo = primer_nodo
        contador = 1
        while nodo:
            marca = " ← ACTUAL" if nodo == self.actual else ""
            print(f"{contador}. {nodo.pagina}{marca}")
            nodo = nodo.siguiente
            contador += 1
    
    def limpiar(self):
        """Limpia todo el historial."""
        self.actual = None
        self.tamaño = 0
        print(" Historial limpiado")
    
    def pagina_actual(self):
        """Muestra la página actual."""
        if self.actual:
            print(f" Página actual: {self.actual.pagina}")
        else:
            print("No hay página actual")
    
    def eliminar_pagina(self, titulo):
        """Elimina una página específica del historial por título."""
        if self.actual is None:
            print(" El historial está vacío")
            return False
        
        # Encontrar el primer nodo
        nodo = self.actual
        while nodo.anterior:
            nodo = nodo.anterior
        
        # Buscar la página a eliminar
        nodo_a_eliminar = None
        while nodo:
            if nodo.pagina.titulo.lower() == titulo.lower():
                nodo_a_eliminar = nodo
                break
            nodo = nodo.siguiente
        
        if nodo_a_eliminar is None:
            print(f" No se encontró la página '{titulo}'")
            return False
        
        # Si es la única página
        if nodo_a_eliminar.anterior is None and nodo_a_eliminar.siguiente is None:
            self.actual = None
            self.tamaño = 0
            print(f" Página '{titulo}' eliminada. Historial vacío.")
            return True
        
        # Si es la página actual
        if nodo_a_eliminar == self.actual:
            if nodo_a_eliminar.anterior:
                # Si hay página anterior, ir a ella
                self.actual = nodo_a_eliminar.anterior
                self.actual.siguiente = None
            elif nodo_a_eliminar.siguiente:
                # Si solo hay página siguiente, ir a ella
                self.actual = nodo_a_eliminar.siguiente
                self.actual.anterior = None
        else:
            # Reconectar los nodos adyacentes
            if nodo_a_eliminar.anterior:
                nodo_a_eliminar.anterior.siguiente = nodo_a_eliminar.siguiente
            if nodo_a_eliminar.siguiente:
                nodo_a_eliminar.siguiente.anterior = nodo_a_eliminar.anterior
        
        self.tamaño -= 1
        print(f" Página '{titulo}' eliminada del historial")
        return True

def menu():
    print("\n" + "="*50)
    print(" HISTORIAL DE NAVEGACIÓN SIMPLE")
    print("="*50)
    print("1. Visitar página")
    print("2. Ver historial")
    print("3. Atrás")
    print("4. Adelante")
    print("5. Página actual")
    print("6. Eliminar página específica")
    print("7. Limpiar historial")
    print("0. Salir")

def main():
    historial = Historial()
    
    while True:
        menu()
        opcion = input("\nElige una opción: ").strip()
        
        if opcion == "0":
            print(" ¡Hasta luego!")
            break
        
        elif opcion == "1":
            titulo = input("Título de la página: ").strip()
            url = input("URL: ").strip()
            if titulo and url:
                historial.visitar(titulo, url)
            else:
                print(" Título y URL son obligatorios")
        
        elif opcion == "2":
            historial.mostrar_historial()
        
        elif opcion == "3":
            historial.atras()
        
        elif opcion == "4":
            historial.adelante()
        
        elif opcion == "5":
            historial.pagina_actual()
        
        elif opcion == "6":
            titulo = input("Título de la página a eliminar: ").strip()
            if titulo:
                historial.eliminar_pagina(titulo)
            else:
                print(" Debes ingresar un título")
        
        elif opcion == "7":
            historial.limpiar()
        
        else:
            print(" Opción no válida")

if __name__ == "__main__":
    main()
