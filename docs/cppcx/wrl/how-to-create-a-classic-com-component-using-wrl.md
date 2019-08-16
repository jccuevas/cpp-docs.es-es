---
title: Procedimiento Creación de un componente COM clásico mediante WRL
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 5efe7690-90d5-4c3c-9e53-11a14cefcb19
ms.openlocfilehash: ec762b07caa30ce9aa6f4c67f84bb66ae884a7cf
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498388"
---
# <a name="how-to-create-a-classic-com-component-using-wrl"></a>Procedimiento Creación de un componente COM clásico mediante WRL

Puede usar la biblioteca de C++ plantillas de Windows Runtime (WRL) para crear componentes básicos de com clásico para su uso en aplicaciones de escritorio, además de usarlo para aplicaciones plataforma universal de Windows (UWP). Para la creación de componentes COM, la biblioteca C++ de plantillas de Windows Runtime puede requerir menos código que la ATL. Para obtener información sobre el subconjunto de COM que C++ admite la biblioteca de plantillas de Windows Runtime, vea [Windows Runtime C++ Template Library (WRL)](windows-runtime-cpp-template-library-wrl.md).

En este documento se muestra cómo usar la C++ biblioteca de plantillas de Windows Runtime para crear un componente com básico. Aunque puede usar el mecanismo de implementación que mejor se adapte a sus necesidades, este documento también muestra una forma básica de registrar y usar el componente COM de una aplicación de escritorio.

### <a name="to-use-the-windows-runtime-c-template-library-to-create-a-basic-classic-com-component"></a>Para usar el Windows Runtime C++ biblioteca de plantillas para crear un componente com clásico básico

1. En Visual Studio, cree un proyecto de **solución en blanco** . Asigne un nombre al proyecto, por `WRLClassicCOM`ejemplo,.

2. Agregue un **proyecto de Win32** a la solución. Asigne un nombre al proyecto, por `CalculatorComponent`ejemplo,. En la pestaña Configuración de la **aplicación** , seleccione **dll**.

3. Agregue un archivo de **archivo MIDL (. idl)** al proyecto. Asigne un nombre al archivo, por `CalculatorComponent.idl`ejemplo,.

4. Agregue este código a CalculatorComponent.idl:

   [!code-cpp[wrl-classic-com-component#1](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_1.idl)]

5. En CalculatorComponent.cpp, defina la clase `CalculatorComponent`. La `CalculatorComponent` clase hereda de [Microsoft:: WRL:: RuntimeClass](runtimeclass-class.md). [Microsoft:: WRL:: runtimeclassflags (\<ClassicCom >](runtimeclassflags-structure.md) especifica que la clase se deriva de [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) y no de [IInspectable](/windows/win32/api/inspectable/nn-inspectable-iinspectable). (`IInspectable` solo está disponible para Windows Runtime componentes de la aplicación). crea un generador para la clase que se puede usar con funciones como [CoCreateInstance.](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance) `CoCreatableClass`

   [!code-cpp[wrl-classic-com-component#2](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_2.cpp)]

6. Use el código siguiente para reemplazar el código en `dllmain.cpp`. Este archivo define las funciones de exportación del archivo DLL. Estas funciones usan la clase [Microsoft:: WRL:: module](module-class.md) para administrar los generadores de clases para el módulo.

   [!code-cpp[wrl-classic-com-component#3](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_3.cpp)]

7. Agregue un archivo **de definición de módulo (. def)** al proyecto. Asigne un nombre al archivo, por `CalculatorComponent.def`ejemplo,. Este archivo proporciona al enlazador los nombres de las funciones que se exportarán.

8. Agregue este código a CalculatorComponent.def:

    ```
    LIBRARY

    EXPORTS
        DllGetActivationFactory PRIVATE
        DllGetClassObject       PRIVATE
        DllCanUnloadNow         PRIVATE
    ```

9. Agregue runtimeobject.lib a la línea del enlazador. Para obtener información sobre cómo hacerlo, vea [. Archivos lib como entrada del vinculador](../../build/reference/dot-lib-files-as-linker-input.md).

### <a name="to-consume-the-com-component-from-a-desktop-app"></a>Para usar el componente COM de una aplicación de escritorio

1. Registre el componente COM con el Registro de Windows. Para ello, cree un archivo de entradas de registro, asígnele `RegScript.reg`un nombre y agregue el texto siguiente. `C:\temp\WRLClassicCOM\Debug\CalculatorComponent.dll`Reemplace  *\<la ruta de acceso de dll >* por la ruta de acceso del archivo dll, por ejemplo,.

    ```
    Windows Registry Editor Version 5.00

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}]
    @="CalculatorComponent Class"

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\InprocServer32]
    @="<dll-path>"
    "ThreadingModel"="Apartment"

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\Programmable]

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\TypeLib]
    @="{9D3E6826-CB8E-4D86-8B14-89F0D7EFCD01}"

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\Version]
    @="1.0"
    ```

2. Ejecute RegScript. reg o agréguelo al **evento posterior a la compilación**del proyecto. Para obtener más información, vea [cuadro de diálogo línea de comandos del evento anterior/posterior a la](/visualstudio/ide/reference/pre-build-event-post-build-event-command-line-dialog-box)compilación.

3. Agregue un proyecto de **aplicación de consola Win32** a la solución. Asigne un nombre al proyecto, por `Calculator`ejemplo,.

4. Use este código para reemplazar el contenido de `Calculator.cpp`:

   [!code-cpp[wrl-classic-com-component#6](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_6.cpp)]

## <a name="robust-programming"></a>Programación sólida

En este documento se utilizan funciones COM estándar para demostrar que puede usar la C++ biblioteca de plantillas de Windows Runtime para crear un componente com y ponerlo a disposición de cualquier tecnología habilitada para com. También puede usar Windows Runtime C++ tipos de biblioteca de plantillas como [Microsoft:: WRL:: ComPtr](comptr-class.md) en la aplicación de escritorio para administrar la duración de com y otros objetos. En el código siguiente se usa C++ la biblioteca de plantillas de Windows Runtime para administrar `ICalculatorComponent` la duración del puntero. La clase `CoInitializeWrapper` es un contenedor RAII que garantiza que la biblioteca COM se libera y también que la duración de la biblioteca COM sobrevive al objeto de puntero inteligente `ComPtr`.

[!code-cpp[wrl-classic-com-component#7](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_7.cpp)]

## <a name="see-also"></a>Vea también

[Biblioteca de plantillas C++ de Windows en tiempo de ejecución (WRL)](windows-runtime-cpp-template-library-wrl.md)