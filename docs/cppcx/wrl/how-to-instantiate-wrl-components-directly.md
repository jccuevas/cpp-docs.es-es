---
title: 'Cómo: Crear instancias de componentes WRL directamente'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1a9fa011-0cee-4abf-bf83-49adf53ff906
ms.openlocfilehash: f291e982d7f77c63821e5943a5867662ccd1b4fa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213907"
---
# <a name="how-to-instantiate-wrl-components-directly"></a>Cómo: Crear instancias de componentes WRL directamente

Aprenda a usar Windows Runtime C++ las funciones[Microsoft:: WRL:: make](make-function.md) y [microsoft:: WRL::D etalles:: MakeAndInitialize](makeandinitialize-function.md) para crear instancias de un componente desde el módulo que lo define.

La creación de instancias de componentes directamente permite reducir la sobrecarga cuando no se necesitan generadores de clases u otros mecanismos. Puede crear instancias de un componente directamente en las aplicaciones Plataforma universal de Windows y en las aplicaciones de escritorio.

Para obtener información sobre cómo usar C++ Windows Runtime biblioteca de plantillas para crear un componente com clásico y crear una instancia de él desde una aplicación de escritorio externa, consulte [Cómo: crear un componente com clásico](how-to-create-a-classic-com-component-using-wrl.md).

En este documento se muestran dos ejemplos. El primer ejemplo utiliza la función `Make` para crear una instancia de un componente. El segundo ejemplo utiliza la función `MakeAndInitialize` para crear una instancia de un componente que pueden producir errores durante la construcción. (Dado que COM normalmente usa Valores HRESULT, en lugar de excepciones, para indicar errores, un tipo COM no se produce normalmente en su constructor. `MakeAndInitialize` permite que un componente valide sus argumentos de construcción mediante el método `RuntimeClassInitialize`). Ambos ejemplos definen una interfaz de registrador básica e implementan esa interfaz definiendo una clase que escribe mensajes en la consola.

> [!IMPORTANT]
> No se puede usar el operador `new` para crear instancias C++ de los componentes de la biblioteca de plantillas Windows Runtime. Por tanto, se recomienda usar siempre `Make` o `MakeAndInitialize` para crear instancias de un componente directamente.

### <a name="to-create-and-instantiate-a-basic-logger-component"></a>Para crear un componente básico de registrador y crear instancias del mismo

1. En Visual Studio, cree un proyecto de **aplicación de consola Win32** . Asigne un nombre al proyecto, por ejemplo, *WRLLogger*.

2. Agregue un archivo de **archivo MIDL (. idl)** al proyecto, asigne un nombre al archivo `ILogger.idl`y, a continuación, agregue este código:

   [!code-cpp[wrl-logger-make#1](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_1.idl)]

3. Use el código siguiente para reemplazar el contenido de `WRLLogger.cpp`.

   [!code-cpp[wrl-logger-make#2](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_2.cpp)]

### <a name="to-handle-construction-failure-for-the-basic-logger-component"></a>Para controlar el error de construcción del componente básico de registrador

1. Utilice el código siguiente para reemplazar la definición de la clase `CConsoleWriter`. Esta versión contiene una variable miembro privada de cadena y reemplaza el método `RuntimeClass::RuntimeClassInitialize`. `RuntimeClassInitialize` produce un error si se produce un error en la llamada a `SHStrDup`.

   [!code-cpp[wrl-logger-makeandinitialize#1](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_3.cpp)]

2. Utilice el código siguiente para reemplazar la definición de `wmain`. Esta versión usa `MakeAndInitialize` para crear una instancia del objeto `CConsoleWriter` y comprueba el resultado HRESULT.

   [!code-cpp[wrl-logger-makeandinitialize#2](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_4.cpp)]

## <a name="see-also"></a>Consulte también

[Biblioteca de plantillas C++ de Windows en tiempo de ejecución (WRL)](windows-runtime-cpp-template-library-wrl.md)<br/>
[Microsoft:: WRL:: make](make-function.md)<br/>
[Microsoft:: WRL::D etalles:: MakeAndInitialize](makeandinitialize-function.md)
