---
title: "Cómo: crear un componente COM clásico mediante WRL | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 5efe7690-90d5-4c3c-9e53-11a14cefcb19
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4b665ae9ce10b4fbf5bd1baa7563e0f94b7fb991
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="how-to-create-a-classic-com-component-using-wrl"></a>Cómo: Crear un componente COM clásico mediante WRL
Puede usar la biblioteca de plantillas de C++ (WRL) de Windows en tiempo de ejecución para crear componentes COM clásicos básicos para su uso en aplicaciones de escritorio, además de usar para las aplicaciones de la plataforma Universal de Windows (UWP). Para la creación de componentes COM, la biblioteca de plantillas de C++ de Windows en tiempo de ejecución puede requerir menos código que ATL. Para obtener información sobre un subconjunto de COM, que es compatible con la biblioteca de plantillas de C++ de Windows en tiempo de ejecución, consulte [biblioteca de plantillas de C++ (WRL) de Windows en tiempo de ejecución](../windows/windows-runtime-cpp-template-library-wrl.md).  
  
 Este documento muestra cómo usar la biblioteca de plantillas de C++ de Windows en tiempo de ejecución para crear un componente COM básico. Aunque puede usar el mecanismo de implementación que mejor se adapte a sus necesidades, este documento también muestra una forma básica de registrar y usar el componente COM de una aplicación de escritorio.  
  
### <a name="to-use-the-windows-runtime-c-template-library-to-create-a-basic-classic-com-component"></a>Usar la biblioteca de plantillas de C++ de Windows en tiempo de ejecución para crear un componente COM clásico básico  
  
1.  En Visual Studio, cree un **solución en blanco** proyecto. Nombre del proyecto, por ejemplo, `WRLClassicCOM`.  
  
2.  Agregar un **proyecto Win32** a la solución. Nombre del proyecto, por ejemplo, `CalculatorComponent`. En el **configuración de la aplicación** ficha, seleccione **DLL**.  
  
3.  Agregar un **archivo Midl (.idl)** archivo al proyecto. Nombre del archivo, por ejemplo, `CalculatorComponent.idl`.  
  
4.  Agregue este código a CalculatorComponent.idl:  
  
     [!code-cpp[wrl-classic-com-component#1](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_1.idl)]  
  
5.  En CalculatorComponent.cpp, defina la clase `CalculatorComponent`. El `CalculatorComponent` clase hereda de [Microsoft::WRL::RuntimeClass](../windows/runtimeclass-class.md). [Microsoft::WRL::RuntimeClassFlags\<ClassicCom >](../windows/runtimeclassflags-structure.md) especifica que la clase se deriva de [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509\(v=vs.85\).aspx) y no [IInspectable](http://msdn.microsoft.com/library/br205821\(v=vs.85\).aspx). (`IInspectable` está disponible solamente para los componentes de aplicación de Windows en tiempo de ejecución.) `CoCreatableClass` crea un generador para la clase que puede utilizar con funciones como [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615\(v=vs.85\).aspx).  
  
     [!code-cpp[wrl-classic-com-component#2](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_2.cpp)]  
  
6.  Use el código siguiente para reemplazar el código de dllmain.cpp. Este archivo define las funciones de exportación del archivo DLL. Estas funciones usan la [Microsoft::WRL::Module](../windows/module-class.md) clase para administrar los generadores de clases para el módulo.  
  
     [!code-cpp[wrl-classic-com-component#3](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_3.cpp)]  
  
7.  Agregar un **archivo de definición de módulo (.def)** archivo al proyecto. Nombre del archivo, por ejemplo, `CalculatorComponent.def`. Este archivo proporciona al enlazador los nombres de las funciones que se exportarán.  
  
8.  Agregue este código a CalculatorComponent.def:  
  
    ```
    LIBRARY

    EXPORTS
        DllGetActivationFactory PRIVATE
        DllGetClassObject       PRIVATE
        DllCanUnloadNow         PRIVATE  
    ```

9. Agregue runtimeobject.lib a la línea del enlazador. Para obtener información sobre cómo hacerlo, consulte [. Lib archivos como entrada del vinculador](../build/reference/dot-lib-files-as-linker-input.md).  
  
### <a name="to-consume-the-com-component-from-a-desktop-app"></a>Para usar el componente COM de una aplicación de escritorio  
  
1.  Registre el componente COM con el Registro de Windows. Para ello, cree un archivo de entradas de registro, asígnele el nombre `RegScript.reg`y agregue el siguiente texto. Reemplace  *\<dll-path >* con la ruta de acceso del archivo DLL, por ejemplo, `C:\\temp\\WRLClassicCOM\\Debug\\CalculatorComponent.dll`.  
  
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
  
2.  Ejecute RegScript.reg o agréguelo a su proyecto **evento posterior a la compilación**. Para obtener más información, consulte [anterior/posterior a la compilación eventos línea de comandos cuadro de diálogo](/visualstudio/ide/reference/pre-build-event-post-build-event-command-line-dialog-box).  
  
3.  Agregar un **aplicación de consola Win32** proyecto a la solución. Nombre del proyecto, por ejemplo, `Calculator`.  
  
4.  Use este código para reemplazar el contenido de Calculator.cpp:  
  
     [!code-cpp[wrl-classic-com-component#6](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_6.cpp)]  
  
## <a name="robust-programming"></a>Programación sólida  
 Este documento usa funciones COM estándar para demostrar que puede usar la biblioteca de plantillas de C++ de Windows en tiempo de ejecución para crear un componente COM y que esté disponible para cualquier tecnología habilitada para COM. También puede usar los tipos de la biblioteca de plantillas de C++ de Windows en tiempo de ejecución como [Microsoft::WRL::ComPtr](../windows/comptr-class.md) en su aplicación de escritorio para administrar la duración de COM y otros objetos. El código siguiente utiliza la biblioteca de plantillas de C++ de Windows en tiempo de ejecución para administrar la vigencia de la `ICalculatorComponent` puntero. La clase `CoInitializeWrapper` es un contenedor RAII que garantiza que la biblioteca COM se libera y también que la duración de la biblioteca COM sobrevive al objeto de puntero inteligente `ComPtr`.  
  
 [!code-cpp[wrl-classic-com-component#7](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_7.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Biblioteca de plantillas C++ de Windows en tiempo de ejecución (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)