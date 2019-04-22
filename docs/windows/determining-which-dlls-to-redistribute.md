---
title: Determinar qué archivos DLL se redistribuirán
ms.date: 03/25/2019
helpviewer_keywords:
- redistributing DLLs
- DLLs [C++], redistributing
- dependencies [C++], application deployment and
- application deployment [C++], DLL redistribution
- deploying applications [C++], DLL redistribution
ms.assetid: f7a2cb42-fb48-42ab-abd2-b35e2fd5601a
ms.openlocfilehash: dd600e2b3e094b1547badd93596a9dbed2438fb3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58786455"
---
# <a name="determining-which-dlls-to-redistribute"></a>Determinar qué archivos DLL se redistribuirán

Al compilar una aplicación que usa los archivos DLL de biblioteca proporcionados por Visual Studio, los usuarios de la aplicación también deben tener esos archivos DLL en sus equipos para ejecutar la aplicación. Dado que la mayoría de los usuarios probablemente no tengan instalado Visual Studio, debe proporcionarles estos archivos DLL. Visual Studio ofrece estos archivos DLL como *archivos redistribuibles* que se pueden incluir en el instalador de la aplicación.

Para que resulte más fácil incluir los archivos DLL redistribuibles con el programa de instalación, también están disponibles como *paquetes redistribuibles* independientes. Se trata de archivos ejecutables específicos de la arquitectura que usan la implementación central para instalar los archivos redistribuibles en el equipo del usuario. Por ejemplo, vcredist\_x86.exe instala las bibliotecas de 32 bits para x86 equipos, vcredist\_x64.exe instala las bibliotecas de 64 bits para x64 equipos y vcredist\_ARM.exe instala las bibliotecas para los equipos ARM. Se recomienda la implementación central para que Microsoft pueda usar el servicio Windows Update para actualizar estas bibliotecas de forma independiente. Además de la copia en la instalación de Visual Studio, los paquetes redistribuibles actuales están disponibles para la descarga. Para obtener vínculos a los paquetes redistribuibles compatibles más recientes para los conjuntos de herramientas actuales y anteriores, vea [Descargas más recientes compatibles de Visual C++](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads). Se pueden encontrar versiones anteriores específicas de los paquetes redistribuibles si se busca "Paquetes redistribuibles de Visual C++" en el [Centro de descarga de Microsoft](http://go.microsoft.com/fwlink/p/?LinkId=158431).

El número de versión principal del paquete redistribuible que se implemente debe coincidir con la versión del conjunto de herramientas de Visual Studio que se use para crear la aplicación, y el número de versión secundaria debe ser el mismo o superior. Visual Studio 2017 y Visual Studio 2015 tienen números de versión de conjunto de herramientas compatibles, lo que significa que las aplicaciones compiladas con el conjunto de herramientas de Visual Studio 2015 pueden usar los archivos redistribuibles de Visual Studio 2017. Aunque puedan ser compatibles, no se admite el uso de los archivos redistribuibles de 2015 en aplicaciones compiladas con el conjunto de herramientas de 2017. Solo se admite el uso de un paquete redistribuible que sea igual o más reciente que la versión del conjunto de herramientas.

Otra manera de incluir los archivos DLL redistribuibles con el instalador es usar *módulos de combinación*. Estos módulos de Microsoft Installer se incluyen y se instalan con el instalador de la aplicación. Los módulos de combinación para los archivos DLL redistribuibles se encuentran en el directorio de instalación de Visual Studio en \\VC\\Redist\MSVC\\*versión*\\MergeModules\\. En versiones anteriores de Visual Studio, estos archivos se encuentran en el directorio \\Archivos de programa o \\Archivos de programa (x86) en un subdirectorio Common Files\\Merge Modules. Para obtener más información sobre el uso de estos archivos, vea [Redistribuir componentes mediante módulos de combinación](redistributing-components-by-using-merge-modules.md).

Los archivos DLL redistribuibles individuales también se incluyen en la instalación de Visual Studio. De forma predeterminada, se instalan en el directorio de instalación de Visual Studio en la carpeta \\VC\\Redist\\MSVC\\*versión*. Los números de *versión* pueden representar otros números de compilación secundaria de un único conjunto común de archivos redistribuibles. Use la versión más reciente de cualquier archivo DLL de biblioteca, paquete redistribuible o módulo de combinación que se encuentran en estos directorios. Puede usar estas bibliotecas para la implementación local, mediante su instalación en el mismo directorio que la aplicación. No se recomienda la implementación local ya que le hace responsable de entregar actualizaciones de las aplicaciones implementadas. Es preferible la implementación central mediante los paquetes redistribuibles.

Para determinar qué archivos DLL se tienen que redistribuir con la aplicación, recopile una lista de archivos DLL de los que depende la aplicación. Normalmente, estos se muestran como entradas de biblioteca de importación al enlazador. Algunas bibliotecas, como vcruntime y la biblioteca en tiempo de ejecución Universal C (UCRT), se incluyen de forma predeterminada. Si la aplicación o una de sus dependencias usa LoadLibrary para cargar un archivo DLL de manera dinámica, es posible que ese archivo DLL no se muestre en las entradas al enlazador. Una manera de recopilar la lista de archivos DLL cargados de forma dinámica consiste en ejecutar Dependency Walker (depends.exe) en la aplicación, como se describe en [Descripción de las dependencias de una aplicación de Visual C++](understanding-the-dependencies-of-a-visual-cpp-application.md). Desafortunadamente, esta herramienta no está actualizada y puede notificar que no encuentra determinados archivos DLL.

Cuando tenga la lista de dependencias, compárela con la lista vinculada al archivo Redist.txt que se encuentra en el directorio de instalación de Microsoft Visual Studio, o bien con la "lista REDIST" de archivos DLL redistribuibles a los que se hace referencia en la sección "Archivos de código distribuibles" de los Términos de licencia del software de Microsoft para la copia de Visual Studio. Para Visual Studio 2017, vea [Código distribuible para Microsoft Visual Studio 2017 (incluye utilidades, extensibilidad y archivos BuildServer)](http://go.microsoft.com/fwlink/p/?linkid=823098). Para Visual Studio 2015, vea [Código distribuible para Microsoft Visual Studio 2015 y Microsoft Visual Studio 2015 SDK (incluye utilidades y archivos BuildServer)](http://go.microsoft.com/fwlink/p/?linkid=799794). En Visual Studio 2013, la lista está disponible en línea en [Código distribuible para Microsoft Visual Studio 2013 y Microsoft Visual Studio 2013 SDK](http://go.microsoft.com/fwlink/p/?LinkId=313603).

En las versiones de Visual Studio anteriores a Visual Studio 2015, la biblioteca de tiempo de ejecución de C (CRT) se incluye como un archivo DLL redistribuible, en msvc*versión*.dll. A partir de Visual Studio 2015, las funciones de CRT se refactorizaron en vcruntime y UCRT. UCRT es ahora un componente del sistema de Windows 10, administrado por Windows Update. Está disponible en todos los sistemas operativos Windows 10. Para implementar la aplicación en sistemas operativos anteriores, es posible que también tenga que redistribuir UCRT. Una versión anterior de UCRT se incluye en los archivos redistribuibles de Visual Studio, que solo se instala en sistemas operativos anteriores a Windows 10, y solo si no hay instalada ninguna versión de UCRT. Para obtener una versión instalable de UCRT para sistemas de nivel inferior como un paquete de actualización de sistema de Microsoft, vea [Tiempo de ejecución de C universal de Windows 10 ](https://www.microsoft.com/download/details.aspx?id=48234) en el Centro de descarga de Microsoft.

No puede redistribuir todos los archivos que se incluyen en Visual Studio; únicamente está permitido redistribuir los archivos que se especifican en Redist.txt o en la "lista de paquetes redistribuibles" en línea. Las versiones de depuración de las aplicaciones y los distintos archivos DLL de Visual C++ no son redistribuibles. Para obtener más información, vea [Elegir un método de implementación](choosing-a-deployment-method.md).

En la tabla siguiente se describen algunos de los archivos DLL de Visual C++ de los que su aplicación puede depender.

|Biblioteca de Visual C++|Descripción|Se aplica a|
|--------------------------|-----------------|----------------|
|vcruntime*versión*.dll|Biblioteca en tiempo de ejecución para código nativo.|Aplicaciones que usan los servicio de inicio y finalización normales del lenguaje C y C++.|
|vccorlib*versión*.dll|Biblioteca en tiempo de ejecución para código administrado.|Aplicaciones que usan los servicios del lenguaje C++ para código administrado.|
|msvcp*versión*.dll y msvcp*versión*_*punto_número*.dll|Biblioteca estándar de C++ para código nativo.|Aplicaciones que usan la [Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md).|
|concrt*versión*.dll|Biblioteca de runtime de simultaneidad para código nativo.|Aplicaciones que usan el [Runtime de simultaneidad](../parallel/concrt/concurrency-runtime.md).|
|mfc*versión*.dll|Biblioteca MFC (Microsoft Foundation Class).|Aplicaciones que usan la [biblioteca MFC](../mfc/mfc-desktop-applications.md).|
|mfc*versión* *lenguaje*.dll|Recursos de la biblioteca Microsoft Foundation Classes (MFC).|Aplicaciones que usan recursos de lenguaje específicos para MFC.|
|mfc*versión*u.dll|Biblioteca MFC con compatibilidad de Unicode.|Aplicaciones que usan la [biblioteca MFC](../mfc/mfc-desktop-applications.md) y requieren compatibilidad con Unicode.|
|mfcmifc80.dll|Biblioteca de interfaces administradas MFC.|Aplicaciones que usan la [biblioteca MFC](../mfc/mfc-desktop-applications.md) con [controles de Windows Forms](/dotnet/framework/winforms/controls/index).|
|mfcm*versión*.dll|Biblioteca administrada MFC.|Aplicaciones que usan la [biblioteca MFC](../mfc/mfc-desktop-applications.md) con [controles de Windows Forms](/dotnet/framework/winforms/controls/index).|
|mfcm*versión*u.dll|Biblioteca administrada MFC con compatibilidad de Unicode.|Aplicaciones que usan la [biblioteca MFC](../mfc/mfc-desktop-applications.md) con [controles de Windows Forms](/dotnet/framework/winforms/controls/index) y requieren compatibilidad con Unicode.|
|vcamp*versión*.dll|Biblioteca AMP para código nativo.|Aplicaciones que usan el código de la [Biblioteca C++ AMP](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).|
|vcomp*versión*.dll|Biblioteca OpenMP para código nativo.|Aplicaciones que usan el código de la [Biblioteca C++ OpenMP](../parallel/openmp/openmp-in-visual-cpp.md).|

> [!NOTE]
> Ya no es necesario redistribuir Active Template Library como archivo DLL independiente. Su funcionalidad se ha movido a los encabezados y a una biblioteca estática.

Para obtener más información sobre cómo redistribuir estos archivos DLL con la aplicación, vea [Redistribuir archivos de Visual C++](redistributing-visual-cpp-files.md). Para obtener ejemplos, vea [Ejemplos de implementación](deployment-examples.md).

Normalmente, no es necesario redistribuir archivos DLL del sistema porque forman parte del sistema operativo. Sin embargo, puede haber excepciones, por ejemplo, si la aplicación se ejecutará en varias versiones de los sistemas operativos de Microsoft. En este caso, asegúrese de leer los términos de licencia correspondientes. Además, intente actualizar los archivos DLL del sistema a través de Windows Update, los Service Pack o mediante otros paquetes redistribuibles facilitados por Microsoft.

## <a name="see-also"></a>Vea también

[Elegir un método de implementación](choosing-a-deployment-method.md)<br/>
[Implementar aplicaciones de escritorio](deploying-native-desktop-applications-visual-cpp.md)
