---
title: /Zc:threadSafeInit (inicialización estática Local de subprocesos) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- threadSafeInit
- /Zc:threadSafeInit
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- threadSafeInit
- Thread-safe Local Static Initialization
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: a0fc4b34-2cf0-45a7-a642-b8afc4ca19f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 438ce5ba783f646e9c8e61d9b82999ea936532b4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32381153"
---
# <a name="zcthreadsafeinit-thread-safe-local-static-initialization"></a>/Zc:threadSafeInit (inicialización estática Local de subprocesos)

El **/Zc:threadSafeInit** opción del compilador indica al compilador que inicializar las variables locales estáticas (ámbito de función) de una manera segura para subprocesos, lo que elimina la necesidad de sincronización manual. Solo la inicialización es segura para subprocesos. Todavía se deben sincronizar manualmente uso y la modificación de las variables locales estáticas por varios subprocesos. Esta opción está disponible a partir de Visual Studio 2015. De forma predeterminada, Visual Studio permite esta opción.

## <a name="syntax"></a>Sintaxis

> **/Zc:threadSafeInit**[**-**]

## <a name="remarks"></a>Comentarios

En el estándar C ++ 11, las variables de ámbito de bloque con estático o la duración de almacenamiento del subproceso debe se inicializa a cero antes de que realiza cualquier otra tarea de inicialización. La inicialización se produce cuando el control pasa primero por la declaración de la variable. Si se produce una excepción durante la inicialización, la variable se considera que no se ha inicializado y se volverá a intentar la inicialización el siguiente control de tiempo pasa a través de la declaración. Si el control entra en la declaración de manera simultánea con la inicialización, los bloques de ejecución simultánea mientras se completa la inicialización. El comportamiento es indefinido si el control vuelve a introduce la declaración de forma recursiva durante la inicialización. De forma predeterminada, Visual Studio a partir de Visual Studio 2015 implementa este comportamiento estándar. Se puede especificar explícitamente este comportamiento estableciendo el **/Zc:threadSafeInit** opción del compilador.

El **/Zc:threadSafeInit** opción del compilador está activada de forma predeterminada. El [/ permisivo-](permissive-standards-conformance.md) no afecta la opción **/Zc:threadSafeInit**.

Inicialización de subprocesos de las variables locales estáticas se basa en el código implementado en la biblioteca de tiempo de ejecución de C Universal (UCRT). Para evitar depender de la UCRT, o para conservar el comportamiento de inicialización no es segura para subprocesos de versiones de Visual Studio anteriores a Visual Studio 2015, use la **/Zc: threadsafeinit** opción. Si sabe que la seguridad de subprocesos no es necesaria, utilice esta opción para generar un código ligeramente más pequeño y rápido alrededor de las declaraciones locales estáticas.

Las variables locales estáticas subprocesos usan internamente el almacenamiento local de subprocesos (TLS) para ofrecer una ejecución eficaz cuando ya se ha inicializado el método estático. La implementación de esta característica se basa en funciones de compatibilidad de sistema operativo de Windows en Windows Vista y sistemas operativos posteriores. Windows XP, Windows Server 2003 y sistemas operativos anteriores no tiene esta compatibilidad, por lo que no obtienen la ventaja de eficacia. Estos sistemas operativos también tienen un límite inferior en el número de secciones TLS que se pueden cargar. Si se supera la TLS límite de sección puede provocar un bloqueo. Si se trata de un problema en el código, especialmente en el código que se debe ejecutar en sistemas operativos anteriores, use **/Zc: threadsafeinit** para deshabilitar el código de inicialización seguro para subprocesos.

Para obtener más información sobre los problemas de conformidad de Visual C++, vea [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Desde el **configuraciones** menú desplegable, elija **todas las configuraciones de**.

1. Seleccione el **propiedades de configuración** > **C/C++** > **línea de comandos** página de propiedades.

1. Modificar el **opciones adicionales** propiedad para incluir **/Zc:threadSafeInit** o **/Zc: threadsafeinit** y, a continuación, elija **Aceptar**.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)<br/>
[/Zc (Ajuste)](../../build/reference/zc-conformance.md)<br/>
