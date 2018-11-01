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
ms.openlocfilehash: 54bea7b42018637bf868dfdd923b94dd75aa2307
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50559489"
---
# <a name="multithreading-creating-worker-threads-in-mfc"></a>Multithreading: Crear subprocesos de trabajo en MFC

Un subproceso de trabajo se utiliza normalmente para controlar tareas en segundo plano que el usuario no debería tener que esperar para seguir usando la aplicación. Tareas como cálculos repetidos e impresión de fondo constituyen buenos ejemplos de subprocesos de trabajo. Este tema detallan los pasos necesarios para crear un subproceso de trabajo. Entre los temas se incluyen los siguientes:

- [Iniciar el subproceso](#_core_starting_the_thread)

- [Implementar la función controladora](#_core_implementing_the_controlling_function)

- [Ejemplo](#_core_controlling_function_example)

Creación de un subproceso de trabajo es una tarea relativamente sencilla. Solo dos pasos son necesarios para obtener el subproceso en funcionamiento: implementar la función controladora e iniciar el subproceso. No es necesario derivar una clase de [CWinThread](../mfc/reference/cwinthread-class.md). Puede derivar una clase si necesita una versión especial de `CWinThread`, pero no es necesario para la mayoría de los subprocesos de trabajo simples. Puede usar `CWinThread` sin ninguna modificación.

##  <a name="_core_starting_the_thread"></a> Iniciar el subproceso

Hay dos versiones sobrecargadas de `AfxBeginThread`: una que solo se puede crear subprocesos de trabajo y otra que puede crear subprocesos de interfaz de usuario y subprocesos de trabajo. Para iniciar la ejecución del subproceso de trabajo mediante la primera sobrecarga, llame a [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), proporcione la información siguiente:

- La dirección de la función controladora.

- El parámetro que se pasará a la función controladora.

- (Opcional) La prioridad deseada del subproceso. El valor predeterminado es la prioridad normal. Para obtener más información acerca de los niveles de prioridad disponibles, vea [SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) en el SDK de Windows.

- (Opcional) El tamaño de pila deseado para el subproceso. El valor predeterminado para el tamaño de pila es el mismo que el del subproceso creador.

- (Opcional) CREATE_SUSPENDED si desea que el subproceso que se creará en un estado suspendido. El valor predeterminado es 0, es decir, iniciar el subproceso normalmente.

- (Opcional) Los atributos de seguridad deseados. El valor predeterminado es el mismo acceso que el de su subproceso primario. Para obtener más información sobre el formato de esta información de seguridad, consulte [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) en el SDK de Windows.

`AfxBeginThread` crea e inicializa un `CWinThread` objeto automáticamente, lo inicia y devuelve su dirección, por lo que puede hacer referencia a él más adelante. Se realizan comprobaciones en todo el procedimiento para asegurar que todos los objetos queden desasignados correctamente en caso de error en algún momento del proceso de creación.

##  <a name="_core_implementing_the_controlling_function"></a> Implementar la función controladora

La función controladora define el subproceso. Cuando se escribe esta función, el subproceso se inicia y cuando se cierra, finaliza el subproceso. Esta función debe tener el siguiente prototipo:

```
UINT MyControllingFunction( LPVOID pParam );
```

El parámetro es un valor único. El valor de que la función recibe en este parámetro es el valor que se pasó al constructor cuando se creó el objeto de subproceso. La función controladora puede interpretar este valor de cualquier manera que elija. Se puede tratar como un valor escalar o un puntero a una estructura que contiene varios parámetros, o puede omitirse. Si el parámetro hace referencia a una estructura, la estructura puede utilizarse no solo para pasar datos desde el llamador al subproceso, sino también para pasar datos desde el subproceso al llamador. Si usa este tipo de estructura para pasar datos al llamador, el subproceso debe notificar al llamador cuándo están listos los resultados. Para obtener información sobre las comunicaciones entre el subproceso de trabajo al llamador, vea [Multithreading: sugerencias de programación](multithreading-programming-tips.md).

Cuando la función termina, debe devolver un valor UINT que indica la razón de finalización. Normalmente, este código de salida es 0 para indicar éxito con otros valores indican diferentes tipos de errores. Esto es puramente depende de la implementación. Algunos subprocesos pueden mantener los recuentos de uso de objetos y devuelve el número actual de los usos de ese objeto. Para ver cómo las aplicaciones pueden recuperar este valor, consulte [Multithreading: Finalizar subprocesos](multithreading-terminating-threads.md).

Hay algunas restricciones en lo que puede hacer en un programa con multithreading escrito con la biblioteca MFC. Para obtener descripciones de estas restricciones y otras sugerencias sobre cómo usar subprocesos, vea [Multithreading: sugerencias de programación](multithreading-programming-tips.md).

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

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Multithreading: Crear subprocesos de la interfaz de usuario](multithreading-creating-user-interface-threads.md)

## <a name="see-also"></a>Vea también

[Multithreading con C++ y MFC](multithreading-with-cpp-and-mfc.md)