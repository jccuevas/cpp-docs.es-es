---
title: "Importar llamadas a funciones mediante __declspec(dllimport) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__declspec"
  - "dllimport"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec(dllimport) (palabra clave) [C++]"
  - "dllimport (atributo) [C++], importaciones de llamadas a funciones"
  - "llamadas a funciones [C++], importar"
  - "importar llamadas a funciones [C++]"
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Importar llamadas a funciones mediante __declspec(dllimport)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El siguiente ejemplo de código muestra la forma de utilizar **\_declspec\(dllimport\)** para importar llamadas a funciones desde un archivo DLL a una aplicación.  Suponga que `func1` es una función que reside en un archivo DLL independiente del archivo .exe que contiene la función **main**.  
  
 Sin **\_\_declspec\(dllimport\)** y dado el código siguiente:  
  
```  
int main(void)   
{  
   func1();  
}  
```  
  
 el compilador generará un código con la siguiente apariencia:  
  
```  
call func1  
```  
  
 y el vinculador traducirá la llamada en algo similar a:  
  
```  
call 0x4000000         ; The address of 'func1'.  
```  
  
 Si `func1` existe en otro archivo DLL, el vinculador no podrá resolver esto directamente, porque no podrá saber cuál es la dirección de `func1`.  En entornos de 16 bits, el vinculador agrega esta dirección de código a una lista del archivo .exe que el cargador revisaría en tiempo de ejecución con la dirección correcta.  En entornos de 32 y 64 bits, el vinculador genera código thunk del que conoce la dirección.  En un entorno de 32 bits, el código thunk es similar al siguiente:  
  
```  
0x40000000:    jmp DWORD PTR __imp_func1  
```  
  
 Aquí, `imp_func1` es la dirección correspondiente al área de `func1` de la tabla de direcciones de importación del archivo .exe.  De esta forma, el vinculador conoce todas las direcciones.  El cargador sólo tiene que actualizar en tiempo de carga la tabla de direcciones de importación del archivo .exe para que todo funcione correctamente.  
  
 Por tanto, es mejor utilizar **\_\_declspec\(dllimport\)**, ya que el vinculador no genera thunk si no es necesario.  Los thunks aumentan el tamaño del código \(en sistemas RISC, pueden ser varias instrucciones\) y pueden reducir el rendimiento de la memoria caché.  Si indica al compilador que la función está en un archivo DLL, puede generar una llamada indirecta.  
  
 Así, el siguiente fragmento de código:  
  
```  
__declspec(dllimport) void func1(void);  
int main(void)   
{  
   func1();  
}  
```  
  
 genera la siguiente instrucción:  
  
```  
call DWORD PTR __imp_func1  
```  
  
 No hay thunk ni ninguna instrucción `jmp`, por lo que el código será de menor tamaño y más rápido.  
  
 Por otra parte, para las llamadas a función dentro de un archivo DLL, no debería ser necesario utilizar una llamada indirecta.  El usuario ya conoce la dirección de una función.  Puesto que se necesita tiempo y espacio para cargar y almacenar la dirección de la función antes que una llamada indirecta; una llamada directa siempre será más rápida y ocupará menos espacio.  Sólo debe utilizar **\_\_declspec\(dllimport\)** al llamar a funciones de archivo DLL desde fuera del archivo DLL.  No utilice **\_\_declspec\(dllimport\)** en funciones dentro de un archivo DLL cuando lo compile.  
  
## Vea también  
 [Importar a una aplicación](../build/importing-into-an-application.md)