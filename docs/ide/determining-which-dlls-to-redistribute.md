---
title: "Determinar qué archivos DLL se redistribuirán | Documentos de Microsoft"
ms.custom: 
ms.date: 03/13/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- redistributing DLLs
- DLLs [C++], redistributing
- dependencies [C++], application deployment and
- application deployment [C++], DLL redistribution
- deploying applications [C++], DLL redistribution
ms.assetid: f7a2cb42-fb48-42ab-abd2-b35e2fd5601a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a6f942b01dd9379aea0c0ea2ab3751a6f140ef2a
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2018
---
# <a name="determining-which-dlls-to-redistribute"></a>Determinar qué archivos DLL se redistribuirán

Al compilar una aplicación que utiliza los archivos DLL de biblioteca proporcionadas por Visual Studio, los usuarios de la aplicación deben tener también esos archivos DLL en sus equipos para ejecutar la aplicación. Dado que la mayoría de los usuarios probablemente no tengan instalado Visual Studio, debe proporcionarles estos archivos DLL. Visual Studio ofrece estos archivos DLL como *los archivos redistribuibles* que se pueden incluir en el instalador de la aplicación.

Para que sea más fácil de incluir los archivos DLL redistribuibles con el instalador, están disponibles como independiente *paquetes redistribuibles*. Se trata de archivos ejecutables de específicos de la arquitectura que utilizan la implementación central para instalar los archivos redistribuibles en el equipo del usuario. Por ejemplo, vcredist\_x86.exe instala las bibliotecas de 32 bits para x86 equipos, vcredist\_x64.exe instala las bibliotecas de 32 bits y 64 bits para x64 equipos y vcredist\_ARM.exe instala las bibliotecas de ARM equipos. Se recomienda la implementación central dado que Microsoft pueda usar el servicio Windows Update para actualizar estas bibliotecas de forma independiente. Además de la copia de la instalación de Visual Studio, los paquetes redistribuibles actuales están disponibles para su descarga en [VisualStudio.com/Downloads](https://www.visualstudio.com/downloads/) en la sección otras herramientas y marcos.

El número de versión principal del paquete redistribuible que implementa debe coincidir con la versión del conjunto de herramientas de Visual Studio que se utiliza para crear la aplicación. Visual Studio 2017 y Visual Studio 2015 tienen números de versión del conjunto de herramientas compatibles, lo que significa que las aplicaciones compiladas con el conjunto de herramientas de 2015 pueden utilizar los archivos redistribuibles de 2017 Studio Visual. Mientras que pueden ser compatibles, no se admite el uso de los archivos redistribuibles de 2015 en aplicaciones compiladas con el conjunto de herramientas de 2017. Solo se admite el uso de un paquete redistribuible que es igual o posterior a la versión de conjunto de herramientas. Para obtener vínculos a la más reciente compatibles paquetes redistribuibles para conjuntos de herramientas anteriores, consulte [la versión más reciente admite descargas de Visual C++](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads). Versiones anteriores de los paquetes redistribuibles pueden encontrar el [Microsoft Download Center](http://go.microsoft.com/fwlink/p/?LinkId=158431) para "Paquetes redistribuibles de Visual C++".

Otra manera de incluir los archivos DLL redistribuibles con el instalador es usar *módulos de combinación*. Estos módulos de Microsoft Installer se incluye en e instalados por el instalador de la aplicación. Módulos de combinación para los archivos DLL redistribuibles se encuentran en el directorio de instalación de Visual Studio en \\VC\\Redist\MSVC\\*versión*\\MergeModules\\ . En versiones anteriores de Visual Studio, estos archivos se encuentran en su \\archivos de programa o \\directorio de archivos de programa (x86) en los archivos comunes\\subdirectorio de módulos de combinación. Para obtener más información sobre el uso de estos archivos, consulte [Redistribuir componentes mediante el uso de módulos de combinación](../ide/redistributing-components-by-using-merge-modules.md).

Los archivos DLL redistribuibles individuales también se incluyen en la instalación de Visual Studio. De forma predeterminada, se instalan en el directorio de instalación de Visual Studio en el \\VC\\Redist\\MSVC\\*versión* carpeta. El *versión* números pueden representar números de compilación secundaria diferentes de un único conjunto común de los archivos redistribuibles. Utilice la versión más reciente de cualquier archivo DLL de biblioteca, el paquete redistribuible o el módulo de combinación que se encuentran en estos directorios. Puede usar estas bibliotecas para la implementación local, mediante su instalación en el mismo directorio que la aplicación. No se recomienda la implementación local ya que hace responsable de entregar las actualizaciones a las aplicaciones implementadas. Implementación central mediante los paquetes redistribuibles se prefiere.

Para determinar qué archivos DLL se tienen que redistribuir con la aplicación, recopile una lista de archivos DLL de los que depende la aplicación. Normalmente, estos se muestran como importar entradas de la biblioteca al vinculador. Determinadas bibliotecas, como vcruntime y la biblioteca de tiempo de ejecución de C (UCRT) Universal, se incluyen de forma predeterminada. Si la aplicación o una de sus dependencias usa LoadLibrary para cargar dinámicamente un archivo DLL, ese archivo DLL no puede mostrarse en las entradas al vinculador. Una manera de recopilar la lista de archivos DLL cargadas dinámicamente es ejecutar Dependency Walker (depends.exe) en la aplicación, como se describe en [descripción de las dependencias de una aplicación de Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md). Por desgracia, esta herramienta no está actualizada y puede informar de que no se encuentra determinado archivos DLL.

Cuando tenga la lista de dependencias, compárela con la lista vinculada en el archivo Redist.txt que se encuentra en el directorio de instalación de Microsoft Visual Studio, o a la "lista REDIST" de los archivos DLL redistribuibles que se hace referencia en la sección "Archivos de código distribuible" de los términos de licencia del Software de Microsoft para su copia de Visual Studio. Para Visual Studio de 2017, consulte [código distribuible para Microsoft Visual Studio 2017 (incluye utilidades, extensibilidad y archivos BuildServer)](http://go.microsoft.com/fwlink/p/?linkid=823098). Para Visual Studio 2015, vea [código distribuible para Microsoft Visual Studio 2015 y Microsoft Visual Studio 2015 SDK (incluye utilidades y archivos BuildServer)](http://go.microsoft.com/fwlink/p/?linkid=799794). En Visual Studio 2013, la lista está disponible en línea en [código distribuible para Microsoft Visual Studio 2013 y Microsoft Visual Studio 2013 SDK](http://go.microsoft.com/fwlink/p/?LinkId=313603).

En versiones de Visual Studio anteriores a Visual Studio 2015, la biblioteca de tiempo de ejecución de C (CRT) se incluye como un archivo DLL redistribuible, en msvc*versión*.dll. A partir de Visual Studio 2015, las funciones de CRT se refactorizan en vcruntime y el UCRT. El UCRT ahora es un componente del sistema de Windows 10, administrados por Windows Update. Está disponible en todos los sistemas operativos de Windows 10. Para implementar la aplicación en sistemas operativos anteriores, debe redistribuir la UCRT también. Una versión anterior de la UCRT se incluye en los archivos redistribuibles de Visual Studio, que solo se instala en sistemas operativos anteriores a Windows 10, y solo si ya hay instalada ninguna versión de la UCRT. Para obtener una versión instalable de la UCRT para sistemas de nivel inferior como un paquete de actualización de sistema de Microsoft, consulte [tiempo de ejecución de C Universal de Windows 10](https://www.microsoft.com/en-us/download/details.aspx?id=48234) en Microsoft Download Center.

No puede redistribuir todos los archivos que se incluyen en Visual Studio; únicamente está permitido redistribuir los archivos que se especifican en Redist.txt o en la "lista de paquetes redistribuibles" en línea. Las versiones de depuración de las aplicaciones y los distintos archivos DLL de Visual C++ no son redistribuibles. Para obtener más información, consulte [elegir un método de implementación](../ide/choosing-a-deployment-method.md).

En la tabla siguiente se describen algunos de los archivos DLL de Visual C++ de los que su aplicación puede depender.

|Biblioteca de Visual C++|Descripción|Se aplica a|
|--------------------------|-----------------|----------------|
|vcruntime*version*.dll|Biblioteca en tiempo de ejecución para código nativo.|Aplicaciones que usan la normal C y C++ language inicio y finalización servicios.|
|vccorlib*version*.dll|Biblioteca en tiempo de ejecución para código administrado.|Aplicaciones que usan los servicios de lenguaje C++ para código administrado.|
|msvcp*versión*.dll y msvcp*versión*_*dotnumber*.dll|Biblioteca estándar de C++ para código nativo.|Las aplicaciones que utilizan el [biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md).|
|concrt*version*.dll|Biblioteca en tiempo de ejecución de simultaneidad para código nativo.|Las aplicaciones que utilizan el [Runtime de simultaneidad](../parallel/concrt/concurrency-runtime.md).|
|mfc*version*.dll|Biblioteca MFC (Microsoft Foundation Class).|Las aplicaciones que utilizan el [biblioteca MFC](../mfc/mfc-desktop-applications.md).|
|MFC*versión* *lenguaje*.dll|Microsoft Foundation Class (MFC) recursos de biblioteca.|Aplicaciones que utilizan recursos de idioma específicas de MFC.|
|mfc*version*u.dll|Biblioteca MFC con compatibilidad de Unicode.|Las aplicaciones que utilizan el [biblioteca MFC](../mfc/mfc-desktop-applications.md) y requieren la compatibilidad de Unicode.|
|mfcmifc80.dll|Biblioteca de interfaces administradas MFC.|Las aplicaciones que utilizan el [biblioteca MFC](../mfc/mfc-desktop-applications.md) con [controles de Windows Forms](/dotnet/framework/winforms/controls/index).|
|mfcm*version*.dll|Biblioteca administrada MFC.|Las aplicaciones que utilizan el [biblioteca MFC](../mfc/mfc-desktop-applications.md) con [controles de Windows Forms](/dotnet/framework/winforms/controls/index).|
|mfcm*version*u.dll|Biblioteca administrada MFC con compatibilidad de Unicode.|Las aplicaciones que utilizan el [biblioteca MFC](../mfc/mfc-desktop-applications.md) con [controles de Windows Forms](/dotnet/framework/winforms/controls/index) y requieren la compatibilidad de Unicode.|
|vcamp*version*.dll|Biblioteca de AMP para código nativo.|Las aplicaciones que utilizan el [biblioteca de C++ AMP](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md) código.|
|vcomp*version*.dll|Biblioteca de OpenMP para código nativo.|Las aplicaciones que utilizan el [biblioteca de C++ OpenMP](../parallel/openmp/openmp-in-visual-cpp.md) código.|

> [!NOTE]
> Ya no es necesario redistribuir Active Template Library como archivo DLL independiente. Su funcionalidad se ha movido a los encabezados y a una biblioteca estática.

Para obtener más información sobre cómo redistribuir estos archivos DLL con su aplicación, consulte [redistribuir archivos de Visual C++](../ide/redistributing-visual-cpp-files.md). Para obtener ejemplos, vea [ejemplos de implementación](../ide/deployment-examples.md).

Normalmente, no es necesario redistribuir archivos DLL del sistema porque forman parte del sistema operativo. Sin embargo, puede haber excepciones, por ejemplo, si la aplicación se ejecutará en varias versiones de los sistemas operativos de Microsoft. En este caso, asegúrese de leer los términos de licencia correspondientes. Además, intente actualizar los archivos DLL del sistema a través de Windows Update, los Service Pack o mediante otros paquetes redistribuibles facilitados por Microsoft.

## <a name="see-also"></a>Vea también

[Elegir un método de implementación](../ide/choosing-a-deployment-method.md)

[Implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md)
