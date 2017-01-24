---
title: "Comportamiento de la biblioteca en tiempo de ejecuci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_DllMainCRTStartup"
  - "CRT_INIT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CRT_INIT (macro)"
  - "_DllMainCRTStartup (método)"
  - "DllMain (función)"
  - "DLL [C++], función de punto de entrada"
  - "DLL [C++], comportamiento de la biblioteca en tiempo de ejecución"
  - "DLL [C++], secuencia de inicio"
  - "asociación de procesos [C++]"
  - "desasociación de procesos [C++]"
  - "tiempo de ejecución [C++], secuencia de inicio de DLL"
ms.assetid: e06f24ab-6ca5-44ef-9857-aed0c6f049f2
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Comportamiento de la biblioteca en tiempo de ejecuci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El código de la biblioteca en tiempo de ejecución de C\/C\+\+ realiza la secuencia de inicio del archivo DLL, que elimina la necesidad de vinculación a un módulo independiente como ocurría en Windows 3.x.  El código de la biblioteca en tiempo de ejecución de C\/C\+\+ es la función de punto de entrada **\_DllMainCRTStartup** del archivo DLL.  La función **\_DllMainCRTStartup** permite, entre otras cosas, llamar a **\_CRT\_INIT**, que inicializa la biblioteca en tiempo de ejecución de C\/C\+\+ y llama a constructores de C\+\+ en variables estáticas no locales.  Sin esta función, la biblioteca en tiempo de ejecución quedaría en un estado no inicializado.  **\_CRT\_INIT** está disponible para un CRT vinculado estáticamente o para vincular al archivo DLL de CRT Msvcr90.dll desde un archivo DLL de usuario.  
  
 Aunque es posible especificar otra función de punto de entrada mediante la opción de vinculador \/ENTRY:, no es recomendable porque la función de punto de entrada tendría que duplicar todo lo que haga **\_DllMainCRTStartup**.  Al compilar archivos DLL en Visual C\+\+, **\_DllMainCRTStartup** se vinculará automáticamente y no tendrá que especificar una función de punto de entrada mediante la opción de vinculador \/ENTRY:.  
  
 Además de inicializar la biblioteca en tiempo de ejecución de C, **\_DllMainCRTStartup** llama a una función denominada `DllMain`.  En función del tipo de DLL que vaya a compilar, Visual C\+\+ proporcionará la función `DllMain` y la vinculará de forma que **\_DllMainCRTStartup** siempre tenga una función a la que llamar.  Así, si no necesita agregar código de inicialización para el archivo DLL, no tendrá que hacer nada específico cuando compile dicho archivo DLL.  Si tiene que inicializar el archivo DLL, el punto en el que debe agregar el código dependerá del tipo de DLL que vaya a generar.  Para obtener más información, vea [Inicializar un archivo DLL](../build/initializing-a-dll.md).  
  
 La biblioteca en tiempo de ejecución de C\/C\+\+ llama a constructores y destructores en variables estáticas no locales.  Por ejemplo, en el siguiente código fuente de DLL, `Equus` y `Sugar` son dos objetos estáticos no locales de la clase `CHorse`, definida en Horses.h.  No existe ninguna función en el código fuente que contenga llamadas a una función constructora para `CHorse` o a la función destructora, ya que estos objetos se han definido fuera de una función.  Por tanto, las llamadas a estos constructores y destructores deberá realizarla el código en tiempo de ejecución.  El código de la biblioteca en tiempo de ejecución para las aplicaciones también realiza esta función.  
  
```  
#include "horses.h"  
  
CHorse  Equus( ARABIAN, MALE );  
CHorse  Sugar( THOROUGHBRED, FEMALE );  
  
BOOL    WINAPI   DllMain (HANDLE hInst,   
                            ULONG ul_reason_for_call,  
                            LPVOID lpReserved)  
...  
```  
  
 Cada vez que un proceso nuevo intente utilizar el archivo DLL, el sistema operativo creará una copia independiente de los datos del archivo DLL: se llama asociación de proceso.  El código de la biblioteca en tiempo de ejecución para el archivo DLL llama a los constructores para todos los objetos globales, si existen, y después llama a la función `DllMain` con la asociación de procesos activada.  La situación opuesta es la desasociación de procesos: la biblioteca en tiempo de ejecución llama a `DllMain` con la desasociación de procesos activada y después llama a una lista de funciones de finalización, incluidas las funciones `atexit`, destructores para los objetos globales y destructores para los objetos estáticos.  Tenga en cuenta que el orden de los eventos en la asociación de procesos es el inverso de la desasociación de procesos.  
  
 También se llama al código de la biblioteca en tiempo de ejecución durante la asociación de subprocesos y la desasociación de subprocesos, pero este código no realiza la inicialización ni la finalización por si mismo.  
  
## ¿Qué desea hacer?  
  
-   [Inicializar un archivo DLL](../build/initializing-a-dll.md)  
  
## Vea también  
 [Archivos DLL en Visual C\+\+](../build/dlls-in-visual-cpp.md)