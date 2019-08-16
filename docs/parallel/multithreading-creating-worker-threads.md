---
title: 'Multithreading: Crear subprocesos de trabajo en MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- multithreading [C++], worker threads
- background tasks [C++]
- threading [C++], worker threads
- worker threads [C++]
- threading [C++], creating threads
- threading [MFC], worker threads
- threading [C++], user input not required
ms.assetid: 670adbfe-041c-4450-a3ed-be14aab15234
ms.openlocfilehash: c8df3dd9d17819b23362a3b31d8e198883aa9143
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512050"
---
# <a name="multithreading-creating-worker-threads-in-mfc"></a>Multithreading: Crear subprocesos de trabajo en MFC

Un subproceso de trabajo se usa normalmente para controlar las tareas en segundo plano que el usuario no debería tener que esperar para continuar usando la aplicación. Tareas como el recálculo y la impresión en segundo plano son buenos ejemplos de subprocesos de trabajo. En este tema se detallan los pasos necesarios para crear un subproceso de trabajo. Entre los temas se incluyen los siguientes:

- [Iniciar el subproceso](#_core_starting_the_thread)

- [Implementar la función controladora](#_core_implementing_the_controlling_function)

- [Ejemplo](#_core_controlling_function_example)

La creación de un subproceso de trabajo es una tarea relativamente simple. Solo se requieren dos pasos para que se ejecute el subproceso: implementar la función de control e iniciar el subproceso. No es necesario derivar una clase de [CWinThread](../mfc/reference/cwinthread-class.md). Puede derivar una clase si necesita una versión especial de `CWinThread`, pero no es necesaria para la mayoría de los subprocesos de trabajo sencillos. Puede utilizar `CWinThread` sin modificaciones.

##  <a name="_core_starting_the_thread"></a>Iniciar el subproceso

Hay dos versiones sobrecargadas de: `AfxBeginThread`una que solo puede crear subprocesos de trabajo y otra que puede crear subprocesos de interfaz de usuario y subprocesos de trabajo. Para comenzar la ejecución del subproceso de trabajo con la primera sobrecarga, llame a [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread)y proporcione la siguiente información:

- Dirección de la función de control.

- Parámetro que se va a pasar a la función controladora.

- Opta Prioridad deseada del subproceso. El valor predeterminado es la prioridad normal. Para obtener más información sobre los niveles de prioridad disponibles, vea [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) en el Windows SDK.

- (Opcional) El tamaño de pila deseado para el subproceso. El valor predeterminado para el tamaño de pila es el mismo que el del subproceso creador.

- Opta CREATE_SUSPENDED si desea que el subproceso se cree en un estado suspendido. El valor predeterminado es 0, es decir, iniciar el subproceso normalmente.

- (Opcional) Los atributos de seguridad deseados. El valor predeterminado es el mismo acceso que el de su subproceso primario. Para obtener más información acerca del formato de esta información de seguridad, vea [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) en el Windows SDK.

`AfxBeginThread`crea e inicializa un `CWinThread` objeto, lo inicia y devuelve su dirección para que pueda hacer referencia a él más adelante. Se realizan comprobaciones en todo el procedimiento para asegurar que todos los objetos queden desasignados correctamente en caso de error en algún momento del proceso de creación.

##  <a name="_core_implementing_the_controlling_function"></a>Implementar la función controladora

La función controladora define el subproceso. Cuando se especifica esta función, el subproceso se inicia y, cuando se cierra, finaliza el subproceso. Esta función debe tener el prototipo siguiente:

```
UINT MyControllingFunction( LPVOID pParam );
```

El parámetro es un valor único. El valor que la función recibe en este parámetro es el valor que se pasó al constructor cuando se creó el objeto de subproceso. La función controladora puede interpretar este valor de cualquier manera que elija. Se puede tratar como un valor escalar o un puntero a una estructura que contiene varios parámetros, o bien se puede omitir. Si el parámetro hace referencia a una estructura, se puede usar la estructura no solo para pasar datos del llamador al subproceso, sino también para devolver datos del subproceso al llamador. Si utiliza una estructura de este tipo para devolver datos al llamador, el subproceso debe notificar al llamador cuando los resultados estén listos. Para obtener información sobre cómo comunicarse desde el subproceso de trabajo al llamador, vea [multithreading: Sugerencias](multithreading-programming-tips.md)de programación.

Cuando finaliza la función, debe devolver un valor UINT que indique el motivo de la terminación. Normalmente, este código de salida es 0 para indicar que se ha realizado correctamente con otros valores que indican distintos tipos de errores. Esto es exclusivamente dependiente de la implementación. Algunos subprocesos pueden mantener los recuentos de uso de los objetos y devolver el número actual de usos de ese objeto. Para ver cómo las aplicaciones pueden recuperar este valor, [vea multithreading: Finalizando](multithreading-terminating-threads.md)subprocesos.

Hay algunas restricciones sobre lo que puede hacer en un programa multiproceso escrito con la biblioteca MFC. Para obtener descripciones de estas restricciones y otras sugerencias sobre el [uso de subprocesos, vea multithreading: Sugerencias](multithreading-programming-tips.md)de programación.

##  <a name="_core_controlling_function_example"></a>Ejemplo de la función de control

En el ejemplo siguiente se muestra cómo definir una función de control y utilizarla desde otra parte del programa.

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

- [Multithreading: crear subprocesos de interfaz de usuario](multithreading-creating-user-interface-threads.md)

## <a name="see-also"></a>Vea también

[Multithreading con C++ y MFC](multithreading-with-cpp-and-mfc.md)
