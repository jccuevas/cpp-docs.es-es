---
title: "Subprocesamiento m&#250;ltiple: Crear subprocesos de trabajo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tareas en segundo plano [C++]"
  - "subprocesamiento múltiple [C++], subprocesos de trabajo"
  - "subprocesamiento [C++], crear subprocesos"
  - "subprocesamiento [C++], sin intervención del usuario"
  - "subprocesamiento [C++], subprocesos de trabajo"
  - "subprocesamiento [MFC], subprocesos de trabajo"
  - "subprocesos de trabajo [C++]"
ms.assetid: 670adbfe-041c-4450-a3ed-be14aab15234
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Subprocesamiento m&#250;ltiple: Crear subprocesos de trabajo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los subprocesos de trabajo se suelen utilizar con el fin de procesar tareas en segundo plano que no necesiten espera por parte del usuario para continuar usando la aplicación.  Tareas como cálculos repetidos e impresión de fondo constituyen buenos ejemplos de subprocesos de trabajo.  Este tema describe los pasos necesarios para crear subprocesos de trabajo.  Entre los temas se incluyen los siguientes:  
  
-   [Iniciar el subproceso](#_core_starting_the_thread)  
  
-   [Implementar la función controladora](#_core_implementing_the_controlling_function)  
  
-   [Ejemplo](#_core_controlling_function_example)  
  
 Crear un subproceso de trabajo es una tarea relativamente simple.  Sólo se requieren dos pasos para poner el subproceso en funcionamiento: implementar la función controladora e iniciar el subproceso.  No es necesario derivar una clase de [CWinThread](../mfc/reference/cwinthread-class.md).  Puede derivar, si es necesario, una versión especial de `CWinThread`, pero no lo requiere la mayoría de los subprocesos de trabajo simples.  `CWinThread` puede utilizarse sin modificaciones.  
  
##  <a name="_core_starting_the_thread"></a> Iniciar el subproceso  
 Existen dos versiones sobrecargadas de `AfxBeginThread`: una que solo puede crear subprocesos de trabajo y otra que puede crear subprocesos de interfaz de usuario y subprocesos de trabajo.  Para iniciar la ejecución del subproceso de trabajo mediante la primera sobrecarga, llame a [AfxBeginThread](../Topic/AfxBeginThread.md) con la siguiente información:  
  
-   La dirección de la función controladora.  
  
-   El parámetro que se va a pasar a la función controladora.  
  
-   \(Opcional\) El nivel de prioridad deseado para el subproceso.  El valor predeterminado es la prioridad normal.  Para obtener más información acerca de los niveles de prioridad disponibles, vea [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) en [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)].  
  
-   \(Opcional\) El tamaño de pila deseado para el subproceso.  El valor predeterminado para el tamaño de pila es el mismo que el del subproceso creador.  
  
-   \(Opcional\) **CREATE\_SUSPENDED** si se desea crear el subproceso en el estado suspendido.  El valor predeterminado es 0, es decir, iniciar el subproceso normalmente.  
  
-   \(Opcional\) Los atributos de seguridad deseados.  El valor predeterminado es el mismo acceso que el de su subproceso primario.  Para obtener más información acerca del formato de esta información de seguridad, vea [SECURITY\_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) en [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)].  
  
 `AfxBeginThread` crea e inicializa un objeto `CWinThread` automáticamente, lo inicia y devuelve su dirección para poder hacer referencia a él posteriormente.  Se realizan comprobaciones en todo el procedimiento para asegurar que todos los objetos queden desasignados correctamente en caso de error en algún momento del proceso de creación.  
  
##  <a name="_core_implementing_the_controlling_function"></a> Implementar la función controladora  
 La función controladora define el subproceso.  Cuando se inicia esta función, se inicia también el subproceso; y cuando se abandona, el subproceso termina.  Esta función debería presentar el siguiente prototipo:  
  
```  
UINT MyControllingFunction( LPVOID pParam );  
```  
  
 El parámetro tiene un solo valor.  El valor que la función recibe en este parámetro es el valor que se pasó al constructor cuando se creó el objeto de subproceso.  La función controladora puede interpretar este valor de cualquier manera que elija.  Puede tratarlo como valor escalar, como puntero a una estructura que contiene múltiples parámetros, o bien puede pasarlo por alto.  Si el parámetro hace referencia a una estructura, ésta se puede utilizar no sólo para pasar datos al subproceso, sino también para recibir datos del subproceso.  Si utiliza una estructura de este tipo para devolver datos al llamador, el subproceso debe notificar al llamador cuándo están listos los resultados.  Para obtener más información sobre las comunicaciones entre el subproceso de trabajo y el llamador, vea [Multithreading: Sugerencias de programación](../parallel/multithreading-programming-tips.md).  
  
 Cuando la función termina, debe devolver un valor **UINT** que indique el motivo de la terminación.  Normalmente, este código de salida es 0, el cual indica una terminación correcta, mientras que otros valores indican diferentes tipos de error.  No obstante, esto depende de la implementación.  Algunos subprocesos pueden mantener contadores de uso de objetos y devolver el valor correspondiente a ese objeto.  Para saber la forma en que las aplicaciones pueden recuperar este valor, vea [Multithreading: Finalizar subprocesos](../parallel/multithreading-terminating-threads.md).  
  
 Existen algunas restricciones sobre lo que se puede hacer en un programa con multithreading escrito con la biblioteca MFC.  Para obtener una descripción de estas restricciones y otras sugerencias sobre el uso de subprocesos, vea [Multithreading: Sugerencias de programación](../parallel/multithreading-programming-tips.md).  
  
##  <a name="_core_controlling_function_example"></a> Ejemplo de función controladora  
 El ejemplo siguiente muestra cómo definir una función controladora y utilizarla desde otra parte del programa.  
  
```  
UINT MyThreadProc( LPVOID pParam )  
{  
    CMyObject* pObject = (CMyObject*)pParam;  
  
    if (pObject == NULL ||  
        !pObject->IsKindOf(RUNTIME_CLASS(CMyObject)))  
    return 1;   // if pObject is not valid  
  
    // do something with 'pObject'  
  
    return 0;   // thread completed successfully  
}  
  
// inside a different function in the program  
.  
.  
.  
pNewObject = new CMyObject;  
AfxBeginThread(MyThreadProc, pNewObject);  
.  
.  
.  
```  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Multithreading: Crear subprocesos de la interfaz de usuario](../parallel/multithreading-creating-user-interface-threads.md)  
  
## Vea también  
 [Subprocesamiento múltiple con C\+\+ y MFC](../parallel/multithreading-with-cpp-and-mfc.md)