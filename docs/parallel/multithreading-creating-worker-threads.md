---
title: 'Subprocesamiento múltiple: Crear subprocesos de trabajo | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- multithreading [C++], worker threads
- background tasks [C++]
- threading [C++], worker threads
- worker threads [C++]
- threading [C++], creating threads
- threading [MFC], worker threads
- threading [C++], user input not required
ms.assetid: 670adbfe-041c-4450-a3ed-be14aab15234
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 175fc018ddba436f9a331f861a492dcd43e1ec1e
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689277"
---
# <a name="multithreading-creating-worker-threads"></a>Multithreading: Crear subprocesos de trabajo
Un subproceso de trabajo se usa normalmente para controlar tareas en segundo plano que el usuario no debería tener que esperar para seguir usando la aplicación. Tareas como cálculos repetidos e impresión en segundo plano son buenos ejemplos de subprocesos de trabajo. En este tema se detalla los pasos necesarios para crear un subproceso de trabajo. Entre los temas se incluyen los siguientes:  
  
-   [Iniciar el subproceso](#_core_starting_the_thread)  
  
-   [Implementar la función controladora](#_core_implementing_the_controlling_function)  
  
-   [Ejemplo](#_core_controlling_function_example)  
  
 Crear un subproceso de trabajo es una tarea relativamente sencilla. Solo dos pasos necesarios para obtener el subproceso en funcionamiento: implementar la función controladora e iniciar el subproceso. No es necesario derivar una clase de [CWinThread](../mfc/reference/cwinthread-class.md). Puede derivar una clase si necesita una versión especial de `CWinThread`, pero no es necesario para la mayoría de los subprocesos de trabajo simple. Puede usar `CWinThread` sin ninguna modificación.  
  
##  <a name="_core_starting_the_thread"></a> Iniciar el subproceso  
 Existen dos versiones sobrecargadas de `AfxBeginThread`: uno que solo se puede crear subprocesos de trabajo y otro que puede crear subprocesos de interfaz de usuario y subprocesos de trabajo. Para comenzar la ejecución del subproceso de trabajo con la primera sobrecarga, llame a [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), proporcionando la siguiente información:  
  
-   La dirección de la función de control.  
  
-   El parámetro que se pasan a la función controladora.  
  
-   (Opcional) La prioridad deseada del subproceso. El valor predeterminado es la prioridad normal. Para obtener más información acerca de los niveles de prioridad disponibles, vea [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) en el [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
-   (Opcional) El tamaño de pila deseado para el subproceso. El valor predeterminado para el tamaño de pila es el mismo que el del subproceso creador.  
  
-   (Opcional) **CREATE_SUSPENDED** si desea que el subproceso que se creen en un estado suspendido. El valor predeterminado es 0, es decir, iniciar el subproceso normalmente.  
  
-   (Opcional) Los atributos de seguridad deseados. El valor predeterminado es el mismo acceso que el de su subproceso primario. Para obtener más información acerca del formato de esta información de seguridad, consulte [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) en el [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
 `AfxBeginThread` crea e inicializa un `CWinThread` objeto automáticamente, lo inicia y devuelve su dirección por lo que puede hacer referencia a él más adelante. Se realizan comprobaciones en todo el procedimiento para asegurar que todos los objetos queden desasignados correctamente en caso de error en algún momento del proceso de creación.  
  
##  <a name="_core_implementing_the_controlling_function"></a> Implementar la función controladora  
 La función controladora define el subproceso. Cuando se escribe esta función, el subproceso se inicia y cuando se cierra, finaliza el subproceso. Esta función debe tener el siguiente prototipo:  
  
```  
UINT MyControllingFunction( LPVOID pParam );  
```  
  
 El parámetro es un valor único. El valor de que la función recibe en este parámetro es el valor que se pasó al constructor cuando se creó el objeto de subproceso. La función controladora puede interpretar este valor de cualquier manera que elija. Se puede tratar como un valor escalar o un puntero a una estructura que contiene varios parámetros, o puede hacer caso omiso. Si el parámetro hace referencia a una estructura, puede utilizarse la estructura no sólo para pasar datos desde el llamador al subproceso, sino también para pasar datos desde el subproceso al llamador. Si utiliza una estructura de este tipo para pasar datos de vuelta al llamador, el subproceso debe notificar al llamador cuando los resultados están listos. Para obtener información sobre las comunicaciones entre el subproceso de trabajo al autor de llamada, vea [subprocesamiento múltiple: sugerencias de programación](../parallel/multithreading-programming-tips.md).  
  
 Cuando la función termina, debe devolver un **UINT** valor que indica la razón de finalización. Normalmente, este código de salida es 0 para indicar una operación correcta con otros valores indican diferentes tipos de errores. Esto es puramente depende de la implementación. Algunos subprocesos pueden mantener los recuentos de uso de objetos y devolver el número actual de los usos de ese objeto. Para ver cómo las aplicaciones pueden recuperar este valor, vea [Multithreading: Finalizar subprocesos](../parallel/multithreading-terminating-threads.md).  
  
 Hay algunas restricciones en lo que puede hacer en un programa multiproceso escrito con la biblioteca MFC. Para obtener una descripción de estas restricciones y otras sugerencias sobre el uso de subprocesos, vea [subprocesamiento múltiple: sugerencias de programación](../parallel/multithreading-programming-tips.md).  
  
##  <a name="_core_controlling_function_example"></a> Ejemplo de la función de control  
 En el ejemplo siguiente se muestra cómo definir una función controladora y utilizarla desde otra parte del programa.  
  
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
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
  
-   [Multithreading: Crear subprocesos de la interfaz de usuario](../parallel/multithreading-creating-user-interface-threads.md)  
  
## <a name="see-also"></a>Vea también  
 [Multithreading con C++ y MFC](../parallel/multithreading-with-cpp-and-mfc.md)