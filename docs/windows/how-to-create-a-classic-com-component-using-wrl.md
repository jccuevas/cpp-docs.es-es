---
title: "C&#243;mo: Crear un componente COM cl&#225;sico mediante WRL | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: 5efe7690-90d5-4c3c-9e53-11a14cefcb19
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Crear un componente COM cl&#225;sico mediante WRL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede usar [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] ([!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]) para crear componentes COM clásicos básicos destinados a aplicaciones de escritorio y aplicaciones de [!INCLUDE[win8_appstore_long](../build/reference/includes/win8_appstore_long_md.md)]. En la creación de componentes COM, [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] puede requerir menos código que ATL. Para obtener información sobre el subconjunto de COM que el [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] admite, consulte [biblioteca de plantillas de C++ (WRL) de Windows en tiempo de ejecución](../Topic/Windows%20Runtime%20C++%20Template%20Library%20\(WRL\).md).  
  
 Este documento muestra cómo usar la [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] para crear un componente COM básico. Aunque puede usar el mecanismo de implementación que mejor se adapte a sus necesidades, este documento también muestra una forma básica de registrar y usar el componente COM de una aplicación de escritorio.  
  
### <a name="to-use-the-includecppwrlshorttokencppwrlshortmdmd-to-create-a-basic-classic-com-component"></a>Para usar [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] en la creación de un componente COM clásico básico  
  
1.  En Visual Studio, cree un **solución en blanco** proyecto. Nombre del proyecto, por ejemplo, `WRLClassicCOM`.  
  
2.  Agregar un **proyecto Win32** a la solución. Nombre del proyecto, por ejemplo, `CalculatorComponent`. En el **configuración de la aplicación** seleccione **DLL**.  
  
3.  Agregar un **Archivo Midl (.idl)** archivo al proyecto. Nombre del archivo, por ejemplo, `CalculatorComponent.idl`.  
  
4.  Agregue este código a CalculatorComponent.idl:  
  
     [!code-cpp[wrl-classic-com-component#1](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_1.idl)]  
  
5.  En CalculatorComponent.cpp, defina la clase `CalculatorComponent`. La `CalculatorComponent` clase hereda de [Microsoft::WRL::RuntimeClass](../windows/runtimeclass-class.md). [Microsoft::WRL::RuntimeClassFlags \< ClassicCom>](../windows/runtimeclassflags-structure.md) Especifica que la clase se deriva de [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509\(v=vs.85\).aspx) y no [IInspectable](http://msdn.microsoft.com/library/br205821\(v=vs.85\).aspx). (`IInspectable` solo está disponible para [!INCLUDE[win8_appstore_short](../windows/includes/win8_appstore_short_md.md)] componentes de la aplicación.) `CoCreatableClass` crea un generador para la clase que puede utilizarse con funciones como [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615\(v=vs.85\).aspx).  
  
     [!code-cpp[wrl-classic-com-component#2](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_2.cpp)]  
  
6.  Use el código siguiente para reemplazar el código de dllmain.cpp. Este archivo define las funciones de exportación del archivo DLL. Estas funciones usan la [Microsoft::WRL::Module](../windows/module-class.md) clase para administrar los generadores de clases para el módulo.  
  
     [!code-cpp[wrl-classic-com-component#3](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_3.cpp)]  
  
7.  Agregar un **el archivo de definición de módulo (.def)** archivo al proyecto. Nombre del archivo, por ejemplo, `CalculatorComponent.def`. Este archivo proporciona al enlazador los nombres de las funciones que se exportarán.  
  
8.  Agregue este código a CalculatorComponent.def:  
  
     [!CODE [wrl-classic-com-component#4](../CodeSnippet/VS_Snippets_Misc/wrl-classic-com-component#4)]  
  
9. Agregue runtimeobject.lib a la línea del enlazador. Para obtener información sobre cómo hacerlo, consulte [. Archivos lib como entrada del vinculador](../build/reference/dot-lib-files-as-linker-input.md).  
  
### <a name="to-consume-the-com-component-from-a-desktop-app"></a>Para usar el componente COM de una aplicación de escritorio  
  
1.  Registre el componente COM con el Registro de Windows. Para ello, cree un archivo de entradas de registro, asígnele el nombre `RegScript.reg`, y agregue el siguiente texto. Reemplace *\< ruta del archivo dll >* con la ruta de acceso del archivo DLL, por ejemplo, `C:\\temp\\WRLClassicCOM\\Debug\\CalculatorComponent.dll`.  
  
     [!CODE [wrl-classic-com-component#5](../CodeSnippet/VS_Snippets_Misc/wrl-classic-com-component#5)]  
  
2.  Ejecute RegScript.reg o agregarlo a su proyecto **evento posterior a la compilación**. Para obtener más información, consulte [compilación previa o posterior a la compilación eventos línea de comandos cuadro de diálogo](../Topic/Pre-build%20Event-Post-build%20Event%20Command%20Line%20Dialog%20Box.md).  
  
3.  Agregar un **aplicación de consola Win32** proyecto a la solución. Nombre del proyecto, por ejemplo, `Calculator`.  
  
4.  Use este código para reemplazar el contenido de Calculator.cpp:  
  
     [!code-cpp[wrl-classic-com-component#6](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_6.cpp)]  
  
## <a name="robust-programming"></a>Programación sólida  
 Este documento usa funciones COM estándar para demostrar que se puede usar [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] para crear un componente COM y que esté disponible para cualquier tecnología habilitada para COM. También puede utilizar [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] tipos como [Microsoft::WRL::ComPtr](../windows/comptr-class.md) en su aplicación de escritorio para administrar la duración de COM y otros objetos. El siguiente código usa [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] para administrar la duración del puntero `ICalculatorComponent`. La clase `CoInitializeWrapper` es un contenedor RAII que garantiza que la biblioteca COM se libera y también que la duración de la biblioteca COM sobrevive al objeto de puntero inteligente `ComPtr`.  
  
 [!code-cpp[wrl-classic-com-component#7](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_7.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Biblioteca de plantillas C++ de Windows en tiempo de ejecución (WRL)](../Topic/Windows%20Runtime%20C++%20Template%20Library%20\(WRL\).md)