---
title: "Cómo: usar código C++ existente en una aplicación de Plataforma universal de Windows | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 87e5818c-3081-42f3-a30d-3dca2cf0645c
caps.latest.revision: 5
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 220ecd24c6056737d0338cc584663e4664ac81b1
ms.openlocfilehash: 4ea001f8f60a771e46a99960c14201cf6afabc99

---
# <a name="how-to-use-existing-c-code-in-a-universal-windows-platform-app"></a>Cómo: utilizar código C++ existente en una aplicación universal de la plataforma Windows
Quizás la forma más sencilla de conseguir que un programa de escritorio se ejecute en el entorno de UWP es usar las tecnologías de Puente de dispositivo de escritorio. Entre estas se incluye Desktop App Converter, que empaquetará la aplicación existente como una aplicación para UWP sin necesidad de realizar cambios en el código. Para obtener más información, vea [Convertir la aplicación de escritorio en una aplicación para Plataforma universal de Windows (UWP) con el puente de escritorio](https://msdn.microsoft.com/windows/uwp/porting/desktop-to-uwp-root).

El resto de este tema trata sobre cómo migrar bibliotecas de C++ (archivos DLL y bibliotecas estáticas) a la Plataforma universal de Windows (UWP). Podría interesarle hacerlo para que su lógica básica de C++ se pueda usar con varias aplicaciones para UWP. 
  
 Las aplicaciones de UWP se ejecutan en un entorno protegido y, como resultado, no se permiten muchas llamadas de Win32, COM y API de CRT que podrían poner en peligro la seguridad de la plataforma. El compilador puede detectar este tipo de llamadas y generar un error si se utiliza la opción/ZW. Puede usar el Kit de certificación de aplicaciones en la aplicación para detectar código que llama a las API prohibidas. Vea [Uso del kit para la certificación de aplicaciones](https://msdn.microsoft.com/library/windows/apps/hh694081.aspx).  
  
 Si el código fuente está disponible para la biblioteca, puede eliminar las llamadas a API prohibidas. Para obtener más información, incluida una lista de las API permitidas o prohibidas, vea [Win32 y COM para aplicaciones de Windows Runtime y aplicaciones de la Plataforma universal de Windows (UWP)](https://msdn.microsoft.com/library/windows/apps/br205762.aspx) y [Funciones de CRT no admitidas con /ZW](https://msdn.microsoft.com/library/windows/apps/jj606124.aspx). Encontrará algunas alternativas en [Alternativas a las API de Windows en aplicaciones de Windows Runtime y aplicaciones de la Plataforma universal de Windows (UWP)](https://msdn.microsoft.com/library/windows/apps/hh464945.aspx).  
  
 Si intenta agregar una referencia de un proyecto universal de Windows a una biblioteca de escritorio clásica, obtendrá un mensaje de error que indica que la biblioteca no es compatible. En el caso de una biblioteca estática, puede incluir un vínculo a la biblioteca agregando la biblioteca (archivo .lib) a la entrada del enlazador, tal como lo haría en una aplicación clásica de Win32. Para las bibliotecas que solo están disponibles en un archivo binario, esta es la única opción. Hay biblioteca estática vinculada al archivo ejecutable de la aplicación, pero se debe empaquetar en la aplicación el archivo DLL de Win32 que utilizará en la aplicación de UWP incluyéndolo en el proyecto y marcándolo como contenido. Para cargar un archivo DLL de Win32 en una aplicación de la Plataforma universal de Windows, también tiene que llamar a [LoadPackagedLibrary](https://msdn.microsoft.com/library/windows/desktop/hh447159.aspx) en lugar de a LoadLibrary o a LoadLibraryEx.  
  
 Si tiene código fuente para el archivo DLL o para una biblioteca estática, puede volver a compilar con/ZW como un proyecto UWP. Si lo hace, puede agregar una referencia mediante el Explorador de soluciones y utilizarla en aplicaciones de C++ de UWP. En el caso de un archivo DLL, se vincula con la biblioteca de exportación.  
  
 Para exponer la funcionalidad a llamadores en otros lenguajes, puede convertir la biblioteca en un componente de Windows en tiempo de ejecución. Los componentes de Windows Runtime se diferencian de los DLL normales en que incluyen metadatos en forma de archivos .winmd que describen el contenido de la manera en que los consumidores de .NET y JavaScript lo requieren. Para exponer elementos de la API a otros lenguajes, puede agregar construcciones C++/CX, como clases de referencia, y hacerlas públicas o usar la [Biblioteca de plantillas C++ de Windows Runtime (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).  En Windows 10 y versiones posteriores, puede usar la [biblioteca de C++/WinRT](https://github.com/microsoft/cppwinrt) en lugar de C++/CX. 
  
 La descripción anterior no se aplica en el caso de los componentes COM, que deben administrarse de manera diferente. Si tiene un servidor COM en un archivo EXE o DLL, puede usarlo en un proyecto universal de Windows siempre y cuando lo empaquete como un [componente COM sin registro](https://msdn.microsoft.com/library/dd408052.aspx), lo agregue al proyecto como un archivo de contenido y cree instancias del mismo mediante [CoCreateInstanceFromApp](https://msdn.microsoft.com/library/windows/apps/hh404137.aspx). Vea [Using Free-COM DLL in Windows Store C++ Project](http://blogs.msdn.com/b/win8devsupport/archive/2013/05/20/using-free-com-dll-in-windows-store-c-project.aspx) (Usar un archivo DLL de COM gratuito en un proyecto de C++ de la Tienda Windows).  
  
 Si ya tiene una biblioteca COM y quiere migrarla a la Plataforma universal de Windows, puede convertirla en un componente de Windows Runtime mediante la [Biblioteca de plantillas C++ de Windows Runtime (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md). La WRL no admite todas las características de ATL y OLE, por lo que la viabilidad de esta migración dependerá del grado de dependencia del código COM de las características de COM, ATL y OLE que requiera el componente.  
  
 Estas son las distintas formas en que puede utilizar el código C++ existente en proyectos de la plataforma universal de Windows. Algunas formas no requieren que se vuelva a compilar el código con las extensiones del componente (C++ / CX) habilitadas (es decir, con la opción /ZW) y algunas sí; si necesita mantener código en C++ estándar o mantener el entorno de compilación clásico de Win32 para algún código, puede hacerlo, con las opciones de arquitectura adecuadas. Por ejemplo, todo el código que contenga la interfaz de usuario de la plataforma universal de Windows y los tipos que se expondrán a los llamadores de C#, Visual Basic y JavaScript deben estar en los proyectos de aplicaciones de Windows y en los proyectos de componentes de Windows en tiempo de ejecución. El código que debe utilizarse únicamente en C++ (incluido C++/CX) puede encontrarse tanto en un proyecto que se compila con la opción /WX como en un proyecto de C++ estándar. El código exclusivamente binario se puede utilizar vinculándolo como biblioteca estática o empaquetándolo con la aplicación como contenido y cargándolo en un archivo DLL solo si no usa las API prohibidas.  
  
 Independientemente de cuál de estos escenarios de desarrollo elija, debe tener en cuenta el número de definiciones de macro que puede utilizar en el código para que se pueda compilar potencialmente tanto en la plataforma de escritorio clásico de Win32 como en la plataforma universal de Windows.  
  
```cpp  
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PC_APP)  
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PHONE_APP)  
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_APP)  
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_DESKTOP)  
```  
  
 Estas instrucciones se aplican respectivamente a las aplicaciones de la tienda de Windows, de la tienda de Windows Phone, a ambas o a ninguna (solo a las de escritorio clásico de Win32). Estas macros solo están disponibles en el SDK de Windows 8.1 y posterior, por lo que si necesita  compilar el código con las versiones anteriores del SDK de Windows o para otras plataformas, también debería considerar el caso de que ninguna de ellas estén definidas.  
  
 Este tema contiene los siguientes procedimientos.  
  
1.  [Usar un archivo DLL de Win32 en una aplicación de la Plataforma universal de Windows](#BK_Win32DLL)  
  
2.  [Usar una biblioteca estática nativa de C++ en una aplicación para UWP](#BK_StaticLib)  
  
3.  [Convertir una biblioteca de C++ en un componente de Windows Runtime](#BK_WinRTComponent)  
  
##  <a name="a-namebkwin32dlla-using-a-win32-dll-in-a-universal-windows-platform-app"></a><a name="BK_Win32DLL"></a> Usar un archivo DLL de Win32 en una aplicación de la Plataforma universal de Windows  
 Para mayor seguridad y confiabilidad, las aplicaciones universales de Windows se ejecutan en un entorno en tiempo de ejecución restringido, de modo que no puede usar cualquier archivo DLL nativo tal como lo haría en una aplicación de escritorio clásico de Windows. Si tiene código fuente para un archivo DLL, puede migrar el código para que se ejecute en la plataforma universal de Windows. Empiece por cambiar algunos metadatos del archivo de proyecto y la configuración del proyecto para identificar el proyecto como un proyecto de UWP. Debe compilar el código de la biblioteca con la opción/ZW, lo que habilita C++/CX. No se permiten ciertas llamadas a API en las aplicaciones de UWP debido a los controles más estrictos de ese entorno. Vea [Win32 y COM para aplicaciones de Windows Runtime y aplicaciones para Plataforma universal de Windows (UWP)](https://msdn.microsoft.com/library/windows/apps/br205757.aspx).  
  
 El siguiente procedimiento se aplica en el caso de que tenga una DLL nativa que expone funciones mediante __declspec (dllexport).  
  
#### <a name="to-port-a-native-dll-to-the-uwp-without-creating-a-new-project"></a>Portar una DLL nativa a UWP sin crear un nuevo proyecto  
  
1.  Si dispone de una DLL nativa que exporta funciones mediante __declspec (dllexport), puede llamar a estas funciones desde una aplicación UWP recompilando la DLL como un proyecto UWP. Por ejemplo, supongamos que tenemos una DLL que exporta un par de clases y sus métodos, con un código como el siguiente archivo de encabezado:  
  
    ```  
    // giraffe.h  
    #pragma once  
  
    #ifdef _DLL  
    #define GIRAFFE_API __declspec(dllexport)  
    #else  
    #define GIRAFFE_API   
    #endif  
  
    GIRAFFE_API int giraffeFunction();  
  
    class Giraffe  
    {  
        int id;  
            Giraffe(int id_in);  
        friend class GiraffeFactory;  
  
    public:  
        GIRAFFE_API int GetID();  
    };  
  
    class GiraffeFactory  
    {  
        static int nextID;  
    
    public:  
        GIRAFFE_API GiraffeFactory();  
        GIRAFFE_API static int GetNextID();  
        GIRAFFE_API static Giraffe* Create();  
   };  
    ```  
  
     Y el siguiente archivo de código:  
  
    ```  
    // giraffe.cpp  
    #include "stdafx.h"  
    #include "giraffe.h"  
  
    Giraffe::Giraffe(int id_in) : id(id_in)  
    {  
    }  
  
    int Giraffe::GetID()  
    {  
      return id;  
    }  
  
    int GiraffeFactory::nextID = 0;  
  
    GiraffeFactory::GiraffeFactory()  
    {  
        nextID = 0;  
    }  
  
    int GiraffeFactory::GetNextID()  
    {  
        return nextID;  
    }  
  
    Giraffe* GiraffeFactory::Create()  
    {  
        return new Giraffe(nextID++);  
    }  
  
    int giraffeFunction();  
    ```  
  
     Todo lo demás en el proyecto (stdafx.h, dllmain.cpp) forma parte de la plantilla de proyecto estándar de Win32. Si quiere seguir adelante pero todavía no quiere usar estos pasos en su propio archivo DLL, pruebe a crear un proyecto de Win32, seleccione DLL en el Asistente del proyecto y luego agregue un archivo de encabezado giraffe.h y un archivo de código giraffe.cpp. Luego, copie el contenido del código de este paso en los archivos apropiados.  
  
     El código define la macro GIRAFFE_API que se resuelve como __declspec (dllexport) cuando se define _DLL (es decir, cuando se compila el proyecto como un archivo DLL).  
  
2.  Abra las propiedades del proyecto DLL y establezca la configuración en **Todas las configuraciones**.  
  
3.  En las propiedades del proyecto, en **C/C++**, en la pestaña **General**, establezca **Usar extensión de Windows Runtime** en **Sí (/ZW)**. Esto habilita las extensiones de componente (C++/CX).  
  
4.  En el **Explorador de soluciones**, seleccione el nodo del proyecto, abra el menú contextual y elija **Descargar el proyecto**. A continuación, abra el menú contextual en el nodo del proyecto descargado y elija Editar el archivo de proyecto. Busque el elemento de WindowsTargetPlatformVersion y reemplácelo por los siguientes elementos.  
  
    ```xml  
    <AppContainerApplication>true</AppContainerApplication>  
    <ApplicationType>Windows Store</ApplicationType>  
    <WindowsTargetPlatformVersion>10.0.10156.0</WindowsTargetPlatformVersion>  
    <WindowsTargetPlatformMinVersion>10.0.10156.0</WindowsTargetPlatformMinVersion>  
    <ApplicationTypeRevision>10.0</ApplicationTypeRevision>  
    ```  
  
     Cierre el archivo .vcxproj, vuelva a abrir el menú contextual y elija **Volver a cargar el proyecto**.  
  
     Ahora, el Explorador de soluciones identifica el proyecto como un proyecto de Windows universal.  
  
5.  Asegúrese de que el nombre de archivo del encabezado precompilado es correcto. En la sección Encabezados precompilados, cambie el archivo de encabezado precompilado de pch.h a stdafx.h. Si no lo hace, verá el siguiente error.  
  
    ```Output  
    error C2857: '#include' statement specified with the /Ycpch.h command-line option was not found in the source file  
    ```  
  
     El problema es que los proyectos de Windows universales utilizan una nomenclatura diferente para el archivo de encabezado precompilado.  
  
6.  Compile el proyecto. Podrían aparecer algunos errores acerca de opciones de línea de comandos incompatibles. Por ejemplo, la opción Habilitar recompilación mínima (/Gm) se establece de forma predeterminada en muchos proyectos de C++ y no es compatible con /ZW.  
  
     Algunas funciones no están disponibles al compilar para la Plataforma universal de Windows. Verá errores del compilador acerca de cualquier problema. Resuélvalos hasta que tenga una compilación limpia.  
  
7.  Para usar el archivo DLL en una aplicación para UWP en la misma solución, abra el menú contextual del nodo del proyecto de UWP y seleccione **Agregar, Referencia**.  
  
     En **Proyectos, Solución**, active la casilla que se encuentra junto al proyecto DLL y seleccione el botón **Aceptar**.  
  
8.  Incluya los archivos de encabezado de la biblioteca en el archivo pch.h de la aplicación de UWP.  
  
    ```  
    #include "..\MyNativeDLL\giraffe.h"  
    ```  
  
9. Agregue código como de costumbre en el proyecto de UWP para invocar funciones y crear tipos en el archivo DLL.  
  
    ```  
    MainPage::MainPage()  
    {  
        InitializeComponent();  
        GiraffeFactory gf;  
        Giraffe* g = gf.Create();  
        int id = g->GetID();  
    }  
  
    ```  
  
##  <a name="a-namebkstaticliba-using-a-native-c-static-library-in-a-uwp-app"></a><a name="BK_StaticLib"></a> Usar una biblioteca estática nativa de C++ en una aplicación para UWP  
 Puede utilizar una biblioteca estática de C++ nativa en un proyecto UWP, pero se deben tener en cuenta algunas restricciones y limitaciones. Empiece por leer este [tema](https://msdn.microsoft.com/library/hh771041.aspx) sobre las bibliotecas estáticas en C++/CX. Puede acceder al código nativo de la biblioteca estática desde su aplicación de UWP, pero no se recomienda crear tipos de referencia pública en ese tipo de biblioteca estática. Si compila una biblioteca estática con la opción /ZW, el bibliotecario (en realidad, el enlazador camuflado) advierte:  
  
```  
LNK4264: archiving object file compiled with /ZW into a static library; note that when authoring Windows Runtime types it is not recommended to link with a static library that contains Windows Runtime metadata  
```  
  
 Sin embargo, puede utilizar una biblioteca estática en una plataforma universal de Windows sin recompilarla con /ZW. No podrá declarar ningún tipo de referencia o utilizar construcciones C++/CX, pero si su objetivo es simplemente utilizar la biblioteca de código nativo, puede hacerlo siguiendo estos pasos.  
  
#### <a name="to-use-a-native-c-static-library-in-a-uwp-project"></a>Utilizar una biblioteca estática nativa de C++ en un proyecto de UWP  
  
1.  En las propiedades del proyecto para el proyecto de UWP, en la sección del enlazador, agregue la ruta de acceso a la biblioteca en la propiedad de entrada. Por ejemplo, en el caso de una biblioteca del proyecto que coloque su salida en *SolutionFolder*\Debug\MyNativeLibrary\MyNativeLibrary.lib, agregue la ruta de acceso relativa `Debug\MyNativeLibrary\MyNativeLibrary.lib`.  
  
2.  Agregue una instrucción include para incluir una referencia al pch.h en el archivo de encabezado del proyecto de UWP y comenzar a agregar el código que utiliza la biblioteca.  
  
    ```  
    #include "..\MyNativeLibrary\giraffe.h"  
    ```  
  
     No agregue una referencia en el nodo **Referencias** del **Explorador de soluciones**. Este mecanismo solo funciona con los componentes de Windows Runtime.  
  
##  <a name="a-namebkwinrtcomponenta-porting-a-c-library-to-a-windows-runtime-component"></a><a name="BK_WinRTComponent"></a> Convertir una biblioteca de C++ en un componente de Windows Runtime  
 Si desea utilizar las API nativas en una biblioteca estática desde una aplicación de UWP y tiene el código fuente de la biblioteca nativa, puede trasladar el código a un componente de Windows en tiempo de ejecución. Ya no será una biblioteca estática, será un archivo DLL. Puede utilizarlo en cualquier aplicación de C++ de UWP, pero a diferencia de las bibliotecas estáticas, puede agregar tipos de referencia y otras construcciones de C++/CX que están disponibles para los clientes en cualquier código de aplicación de UWP, independientemente del lenguaje. Por lo tanto, puede acceder a estos tipos de C#, Visual Basic o JavaScript.  El procedimiento básico consiste en crear un proyecto de componente de Windows en tiempo de ejecución, copiar el código de la biblioteca estática en él y solucionar los errores que surgen al mover el código de una compilación estándar de C++ a una compilación /ZW.  
  
#### <a name="to-port-a-c-library-to-a-windows-runtime-component"></a>Trasladar una biblioteca de C++ a un componente de Windows en tiempo de ejecución  
  
1.  Cree un proyecto de componente de Windows en tiempo de ejecución.  
  
2.  Cierre el proyectos.  
  
3.  En el Explorador de archivos de Windows, busque el proyecto. De forma predeterminada, Visual Studio usa la carpeta Visual Studio 2017\Projects en la carpeta Documentos. Localice el proyecto de biblioteca de C++ que contiene el código que desee traspasar. Copie los archivos de origen (archivos de encabezado, archivos de código y otros recursos, incluidos los de los subdirectorios) desde el proyecto de biblioteca de C++ y péguelos en la carpeta del proyecto, asegurándose de conservar la misma estructura de carpetas.  
  
4.  Vuelva a abrir el proyecto de componente de Windows Runtime, abra el menú contextual del nodo del proyecto en el **Explorador de soluciones** y seleccione **Agregar, Elemento existente**.  
  
5.  Seleccione todos los archivos que va a agregar desde el proyecto original y haga clic en Aceptar. Repita este paso con las subcarpetas si es necesario.  
  
6.  Es posible que ahora haya algún código duplicado. Si tiene más de un encabezado precompilado (por ejemplo, stdafx.h y pch.h), elija el que desea mantener. Copie cualquier código necesario, como incluir instrucciones, en el encabezado que mantenga. Después, elimine el otro y, en las propiedades del proyecto, en **Encabezados precompilados**, asegúrese de que el nombre del archivo de encabezado es correcto.  
  
     Si cambia el archivo para utilizarlo como encabezado precompilado, asegúrese de que las opciones de encabezado precompilado son las adecuadas para cada archivo. Seleccione cada archivo .cpp por orden, abra la ventana de propiedades y asegúrese de que todos están configurados en **Usar (/Yu)**, excepto el encabezado precompilado deseado, que debe configurarse en **Crear (/Yc)**.  
  
7.  Compile el proyecto y resuelva los errores. Estos errores podrían deberse al uso de la opción /ZW, a una nueva versión del SDK de Windows, podrían reflejar problemas de dependencia (como archivos de encabezado de los que depende la biblioteca) o diferencias entre la configuración del proyecto antiguo y el nuevo.  
  
8.  Agregue tipos de referencia pública a su proyecto o convierta los tipos normales en tipos de referencia para exponer los puntos de entrada en la funcionalidad que desea llamar desde las aplicaciones de UWP.  
  
9. Pruebe el componente agregándole una referencia desde un proyecto de aplicación de UWP y agregue algo de código para llamar a las API públicas que creó.  
  
## <a name="see-also"></a>Vea también  
 [Migrar a la Plataforma universal de Windows](../porting/porting-to-the-universal-windows-platform-cpp.md)


<!--HONumber=Feb17_HO4-->


