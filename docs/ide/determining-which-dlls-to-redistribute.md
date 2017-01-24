---
title: "Determinar qu&#233; archivos DLL se redistribuir&#225;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "implementación de aplicaciones [C++], redistribución de DLL"
  - "dependencias [C++], implementación de aplicaciones y"
  - "implementar aplicaciones [C++], redistribución de DLL"
  - "DLL [C++], redistribuir"
  - "redistribuir DLL"
ms.assetid: f7a2cb42-fb48-42ab-abd2-b35e2fd5601a
caps.latest.revision: 31
caps.handback.revision: 31
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Determinar qu&#233; archivos DLL se redistribuir&#225;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Al compilar una aplicación que usa los archivos DLL incluidos en Visual Studio, los usuarios de la aplicación deben tener también esos archivos DLL en sus equipos para ejecutar la aplicación.  Dado que la mayoría de los usuarios probablemente no tengan instalado Visual Studio, debe proporcionarles estos archivos DLL.  Visual Studio ofrece estos archivos DLL como bibliotecas redistribuibles que se pueden incluir en el instalador de la aplicación.  
  
 Los archivos DLL redistribuibles se incluyen con la instalación de Visual Studio.  De forma predeterminada, se instalan en la carpeta Archivos de programa \(x86\)\\Microsoft Visual Studio \<versión\>\\VC\\Redist.  Para que resulte más fácil incluirlos con el programa de instalación, también están disponibles como paquetes redistribuibles independientes en el Centro de descarga de Microsoft.  Se trata de archivos ejecutables que instalan los archivos redistribuibles en el equipo del usuario.  La versión del paquete redistribuible debe coincidir con la versión del conjunto de herramientas de Visual Studio usado para crear la aplicación.  Para encontrar un paquete redistribuible que coincida, busque "Paquetes redistribuibles de Visual C\+\+"en el [Centro de descarga de Microsoft](http://go.microsoft.com/fwlink/p/?LinkId=158431).  
  
 Para determinar qué archivos DLL se tienen que redistribuir con la aplicación, recopile una lista de archivos DLL de los que depende la aplicación.  Una manera de recopilar la lista es ejecutar Dependency Walker \(depends.exe\), tal y como se describe en [Descripción de las dependencias de una aplicación de Visual C\+\+](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md).  
  
 Cuando tenga la lista de dependencias, compárela con la lista en cualquier archivo Redist.txt del directorio de instalación de Microsoft Visual Studio o con la "lista de paquetes redistribuibles" de archivos DLL redistribuibles a los que se hace referencia en la sección "Código distribuible" de los Términos de licencia del software de Microsoft para su copia de Visual Studio.  En Visual Studio 2013, la lista está disponible en línea en [Código distribuible para Microsoft Visual Studio 2013 y Microsoft Visual Studio2013 SDK](http://go.microsoft.com/fwlink/p/?LinkId=313603).  No puede redistribuir todos los archivos que se incluyen en Visual Studio; únicamente está permitido redistribuir los archivos que se especifican en Redist.txt o en la "lista de paquetes redistribuibles" en línea. Las versiones de depuración de las aplicaciones y los distintos archivos DLL de Visual C\+\+ no son redistribuibles.  Para obtener más información, vea [Elegir un método de implementación](../ide/choosing-a-deployment-method.md).  
  
 En la tabla siguiente se describen algunos de los archivos DLL de Visual C\+\+ de los que su aplicación puede depender.  
  
|Biblioteca de Visual C\+\+|Descripción|Se aplica a|  
|--------------------------------|-----------------|-----------------|  
|msvcr*versión*.dll|Biblioteca en tiempo de ejecución de C \(CRT\) para código nativo.|Aplicaciones que usan las [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md).|  
|msvcp*versión*.dll|Biblioteca estándar de C\+\+ para código nativo.|Aplicaciones que utilizan la [Biblioteca estándar de C\+\+](../standard-library/cpp-standard-library-reference.md).|  
|mfc*versión*.dll|Biblioteca MFC \(Microsoft Foundation Class\).|Aplicaciones que utilizan la [biblioteca MFC](../mfc/mfc-desktop-applications.md).|  
|mfc*versión*u.dll|Biblioteca MFC con compatibilidad de Unicode.|Aplicaciones que utilizan la [biblioteca MFC](../mfc/mfc-desktop-applications.md) y requieren la compatibilidad de Unicode.|  
|mfcmifc80.dll|Biblioteca de interfaces administradas MFC.|Aplicaciones que usan la [biblioteca MFC](../mfc/mfc-desktop-applications.md) con [Controles de Windows Forms](../Topic/Windows%20Forms%20Controls.md).|  
|mfcm*versión*.dll|Biblioteca administrada MFC.|Aplicaciones que usan la [biblioteca MFC](../mfc/mfc-desktop-applications.md) con [Controles de Windows Forms](../Topic/Windows%20Forms%20Controls.md).|  
|mfcm*versión*u.dll|Biblioteca administrada MFC con compatibilidad de Unicode.|Aplicaciones que usan la [biblioteca MFC](../mfc/mfc-desktop-applications.md) con [Controles de Windows Forms](../Topic/Windows%20Forms%20Controls.md) y requieren compatibilidad de Unicode.|  
  
> [!NOTE]
>  Ya no es necesario redistribuir Active Template Library como archivo DLL independiente.  Su funcionalidad se ha movido a los encabezados y a una biblioteca estática.  
  
 Para obtener más información sobre cómo redistribuir estos archivos DLL con la aplicación, vea [Redistribuir archivos de Visual C\+\+](../ide/redistributing-visual-cpp-files.md).  Para obtener ejemplos, vea [Ejemplos de implementación](../ide/deployment-examples.md).  
  
 Normalmente, no es necesario redistribuir archivos DLL del sistema porque forman parte del sistema operativo.  Sin embargo, puede haber excepciones, por ejemplo, si la aplicación se ejecutará en varias versiones de los sistemas operativos de Microsoft.  En este caso, asegúrese de leer los términos de licencia correspondientes.  Además, intente actualizar los archivos DLL del sistema a través de Windows Update, los Service Pack o mediante otros paquetes redistribuibles facilitados por Microsoft.  Puede que encuentre paquetes disponibles buscando en el sitio web [Soporte técnico de Microsoft](http://support.microsoft.com/) o el [Centro de descarga de Microsoft](http://go.microsoft.com/fwlink/p/?LinkId=158431).  
  
## Vea también  
 [Elegir un método de implementación](../ide/choosing-a-deployment-method.md)   
 [Implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md)