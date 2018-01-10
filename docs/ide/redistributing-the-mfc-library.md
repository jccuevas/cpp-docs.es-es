---
title: Redistribuir la biblioteca MFC | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC, redistributing
- redistributing MFC library
ms.assetid: 72714ce1-385e-4c1c-afa5-96b03e873866
caps.latest.revision: "32"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9ca153ec9ca079bf13b1c1c1dcedd6e41497307f
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2018
---
# <a name="redistributing-the-mfc-library"></a>Redistribuir la biblioteca MFC
Si vincula dinámicamente la aplicación a la biblioteca MFC, deberá redistribuir la DLL de MFC coincidente. Por ejemplo, si la aplicación MFC compilada con la versión de MFC que se incluye con Visual Studio 2015, deberá redistribuir mfc140.dll o mfc140u.dll, dependiendo de si la aplicación se compila para compatibilidad con Unicode o caracteres estrechos.  
  
> [!NOTE]
>  Se omitieron los archivos mfc140.dll desde el directorio de los archivos redistribuibles de Visual Studio 2015 RTM. Puede usar las versiones instaladas por Visual Studio 2015 en los directorios Windows\system32 y Windows\syswow64 en su lugar.  
  
 Dado que todos los archivos DLL de MFC utilizan la versión compartida de la biblioteca en tiempo de ejecución de C (CRT), también tendrá que redistribuir la biblioteca CRT. La versión de MFC que se incluye con Visual Studio 2015 usa la biblioteca CRT universal, que se distribuye como parte de Windows 10. Para ejecutar una aplicación MFC compilada con Visual Studio 2015 en versiones anteriores de Windows, debe redistribuir el CRT Universal. Para obtener información sobre cómo redistribuir el CRT universal como un componente del sistema operativo o mediante la implementación local, vea [Introducción a la biblioteca CRT Universal](http://go.microsoft.com/fwlink/p/?linkid=617977). Para descargar el CRT universal para la implementación central en versiones compatibles de Windows, consulte [tiempo de ejecución de C Universal de Windows 10](http://go.microsoft.com/fwlink/p/?LinkId=619489). Las versiones específicas de la arquitectura redistribuibles de ucrtbase.dll para la implementación local se encuentran en el SDK de Windows. De forma predeterminada, Visual Studio instala en C:\Program Files (x86) \Windows Kits\10\Redist\ucrt\DLLs\ en un subdirectorio de específicos de la arquitectura.  
  
 Si la aplicación compilada con una versión anterior de la biblioteca MFC, deberá redistribuir el correspondiente archivo DLL de CRT desde el directorio de los archivos redistribuibles. Por ejemplo, si la aplicación MFC compilada con el conjunto de herramientas de Visual Studio 2013 (vc120), debe redistribuir el msvcr120.dll. También tendrá que redistribuir la búsqueda de coincidencias mfc`<version>`u.dll o con mfc`<version>`.dll.  
  
 Si vincula estáticamente la aplicación a MFC (es decir, si especifica **utilizar MFC en una biblioteca estática** en el **General** pestaña en el **páginas de propiedades** cuadro de diálogo), no es necesario para redistribuir una DLL de MFC. Sin embargo, aunque la vinculación estática puede funcionar para probar la implementación interna de las aplicaciones, se recomienda no utilizarla para redistribuir MFC. Para obtener más información acerca de las estrategias recomendadas para la implementación de bibliotecas de Visual C++, vea [elegir un método de implementación](../ide/choosing-a-deployment-method.md).  
  
 Si su aplicación utiliza las clases MFC que implementan el control WebBrowser (por ejemplo, [clase CHtmlView](../mfc/reference/chtmlview-class.md) o [CHtmlEditView Class](../mfc/reference/chtmleditview-class.md)), se recomienda que también instale la versión más reciente de Microsoft Internet Explorer para que el equipo de destino tendrá los archivos de control comunes más recientes. (Como mínimo, se requiere Internet Explorer 4.0.) La información sobre cómo instalar los componentes de Internet Explorer se encuentra disponible en el artículo "Article 185375: How To Create a Single EXE Install of Internet Explorer"" en el sitio web de Soporte Microsoft.  
  
 Si la aplicación utiliza las clases de base de datos MFC (por ejemplo, [clase CRecordset](../mfc/reference/crecordset-class.md) y [CRecordView (clase)](../mfc/reference/crecordview-class.md)), deberá redistribuir ODBC y los controladores ODBC que usa la aplicación. Para obtener más información, consulte [redistribuir archivos de compatibilidad de base de datos](../ide/redistributing-database-support-files.md).  
  
 Si la aplicación MFC utiliza controles de Windows Forms, deberá redistribuir mfcmifc80.dll con la aplicación. Esta DLL es un ensamblado .NET firmado por nombre seguro que se puede redistribuir con una aplicación en la carpeta local de su aplicación o mediante la implementación a la caché de ensamblados Global (GAC) mediante el uso de la [Gacutil.exe (herramienta de caché Global de ensamblados)](/dotnet/framework/tools/gacutil-exe-gac-tool).  
  
 Si redistribuye una DLL de MFC, asegúrese de redistribuir la versión comercial, y no la de depuración. Las versiones de depuración de las DLL no son redistribuibles. Los nombres de las versiones de depuración de los archivos DLL de MFC terminar con una "d", por ejemplo, Mfc140d.dll.  
  
 Puede redistribuir MFC mediante el uso de cualquier VCRedist_*arquitectura*.exe, los módulos de combinación que se instalan con Visual Studio o mediante la implementación de la DLL de MFC en la misma carpeta que la aplicación. Para obtener más información acerca de cómo redistribuir MFC, vea [redistribuir archivos de Visual C++](../ide/redistributing-visual-cpp-files.md).  
  
## <a name="installation-of-localized-mfc-components"></a>Instalación de componentes de MFC localizados  
 Si decide localizar la aplicación instalando una localización DLL de MFC, debe utilizar los archivos redistribuibles de fusión mediante combinación (.msm). Por ejemplo, si desea localizar la aplicación en un x86 equipo, debe combinar Microsoft_VC`<version>`_MFCLOC_x86.msm en el paquete de instalación para un x86 equipo.  
  
 Los archivos .msm redistribuibles contienen los archivos DLL que se utilizan para la localización. Hay un archivo DLL para cada lenguaje compatible. Durante el proceso de instalación se instalan estos archivos DLL en la carpeta %windir%\system32\ del equipo de destino.  
  
 Para obtener más información sobre cómo localizar aplicaciones de MFC, vea [TN057: localización de componentes de MFC](../mfc/tn057-localization-of-mfc-components.md)y también [208983 de artículo: cómo Using MFC LOC DLLs](http://go.microsoft.com/fwlink/p/?linkid=198025) en el sitio Web Microsoft Support.  
  
 Puede redistribuir archivos DLL de localización de MFC si implementa el archivo DLL de MFC en la carpeta local de la aplicación. Para obtener más información acerca de cómo redistribuir bibliotecas de Visual C++, vea [redistribuir archivos de Visual C++](../ide/redistributing-visual-cpp-files.md).  
  
## <a name="see-also"></a>Vea también  
 [Redistribuir archivos de Visual C++](../ide/redistributing-visual-cpp-files.md)