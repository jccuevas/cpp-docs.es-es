---
title: /Zc:threadSafeInit (inicialización estática Local de subprocesos)
ms.date: 03/14/2018
f1_keywords:
- threadSafeInit
- /Zc:threadSafeInit
helpviewer_keywords:
- -Zc compiler options (C++)
- threadSafeInit
- Thread-safe Local Static Initialization
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: a0fc4b34-2cf0-45a7-a642-b8afc4ca19f2
ms.openlocfilehash: 92a1bfa5ec3bab2814397d51e35e617b7666c706
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808344"
---
# <a name="zcthreadsafeinit-thread-safe-local-static-initialization"></a>/Zc:threadSafeInit (inicialización estática Local de subprocesos)

El **/Zc:threadSafeInit** opción del compilador indica al compilador para inicializar las variables locales estáticas (ámbito de función) de una manera segura para subprocesos, eliminando la necesidad de sincronización manual. Solo la inicialización es segura para subprocesos. Todavía se deben sincronizar manualmente uso y modificación de las variables locales estáticas por varios subprocesos. Esta opción está disponible a partir de Visual Studio 2015. De forma predeterminada, Visual Studio habilita esta opción.

## <a name="syntax"></a>Sintaxis

> **/Zc:threadSafeInit**[**-**]

## <a name="remarks"></a>Comentarios

En el estándar C ++ 11, las variables de ámbito de bloque con estático o de duración de almacenamiento thread debe se inicializa a cero antes de cualquier otra inicialización tiene lugar. La inicialización se produce cuando el control pasa primero por la declaración de la variable. Si se produce una excepción durante la inicialización, se considera la variable no inicializada y la inicialización se volverá a intentar el siguiente control del tiempo pasa a través de la declaración. Si el control entra en la declaración de manera simultánea con la inicialización, los bloques de ejecución sea simultánea, mientras se completa la inicialización. El comportamiento es indefinido si el control vuelve a introduce la declaración de forma recursiva durante la inicialización. De forma predeterminada, Visual Studio a partir de Visual Studio 2015 implementa este comportamiento estándar. Se puede especificar explícitamente este comportamiento estableciendo el **/Zc:threadSafeInit** opción del compilador.

El **/Zc:threadSafeInit** opción del compilador está activada de forma predeterminada. El [/ permissive-](permissive-standards-conformance.md) no afecta la opción **/Zc:threadSafeInit**.

Inicialización segura para subprocesos de las variables locales estáticas se basa en el código implementado en la biblioteca en tiempo de ejecución Universal C (UCRT). Para evitar llevar una dependencia en la UCRT, o para conservar el comportamiento de inicialización que no es segura para subprocesos de versiones de Visual Studio anteriores a Visual Studio 2015, use el **/Zc: threadsafeinit** opción. Si sabe que suprocesos no es necesario, utilice esta opción para generar un código ligeramente más pequeño, más rápido en torno a las declaraciones locales estáticas.

Las variables locales estáticas subprocesos utilizan almacenamiento local de subprocesos (TLS) internamente para proporcionar una ejecución eficaz cuando ya se ha inicializado estático. La implementación de esta característica se basa en las funciones de compatibilidad de sistema operativo de Windows en Windows Vista y sistemas operativos posteriores. Windows XP, Windows Server 2003 y sistemas operativos anteriores no tiene esta compatibilidad, por lo que no obtienen la ventaja de la eficacia. Estos sistemas operativos también tienen un límite inferior en el número de secciones TLS que se pueden cargar. Si se supera el TLS límite sección puede provocar un bloqueo. Si se trata de un problema en el código, especialmente en el código que se debe ejecutar en sistemas operativos anteriores, use **/Zc: threadsafeinit** para deshabilitar el código de inicialización seguro para subprocesos.

Para obtener más información sobre los problemas de conformidad de Visual C++, vea [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Desde el **configuraciones** menú desplegable, elija **todas las configuraciones de**.

1. Seleccione el **propiedades de configuración** > **C o C++** > **línea de comandos** página de propiedades.

1. Modificar el **opciones adicionales** propiedad incluir **/Zc:threadSafeInit** o **/Zc: threadsafeinit** y, a continuación, elija **Aceptar**.

## <a name="see-also"></a>Vea también

[Opciones del compilador MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[/Zc (Ajuste)](zc-conformance.md)<br/>
