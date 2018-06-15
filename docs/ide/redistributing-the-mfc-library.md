---
title: Redistribuir la biblioteca MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, redistributing
- redistributing MFC library
ms.assetid: 72714ce1-385e-4c1c-afa5-96b03e873866
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19a49bf18721f605abe0c6e496d3532012c9c92c
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "33340403"
---
# <a name="redistributing-the-mfc-library"></a>Redistribuir la biblioteca MFC
Si vincula dinámicamente la aplicación a la biblioteca MFC, deberá redistribuir el archivo DLL de MFC coincidente. Por ejemplo, si la aplicación MFC se compila mediante la versión de MFC que se incluye con Visual Studio 2015, deberá redistribuir mfc140.dll o mfc140u.dll, en función de si la aplicación se compila para compatibilidad con Unicode o caracteres estrechos.  
  
> [!NOTE]
>  Los archivos mfc140.dll Se omitieron del directorio de archivos redistribuibles en Visual Studio 2015 RTM. En su lugar, puede usar las versiones instaladas por Visual Studio 2015 en los directorios Windows\system32 y Windows\syswow64.  
  
 Como todos los archivos DLL de MFC usan la versión compartida de la biblioteca en tiempo de ejecución de C (CRT), también tendrá que redistribuir la biblioteca CRT. En la versión de MFC que se incluye con Visual Studio 2015 se usa la biblioteca CRT universal, que se distribuye como parte de Windows 10. Para ejecutar una aplicación MFC compilada con Visual Studio 2015 en versiones anteriores de Windows, debe redistribuir la biblioteca CRT universal. Para obtener información sobre cómo redistribuir la biblioteca CRT universal como un componente del sistema operativo o mediante la implementación local, vea [Introducing the Universal CRT](http://go.microsoft.com/fwlink/p/?linkid=617977) (Introducción a la biblioteca CRT universal). Para descargar la biblioteca CRT universal para la implementación central en versiones compatibles de Windows, vea [Tiempo de ejecución de C universal de Windows 10](http://go.microsoft.com/fwlink/p/?LinkId=619489). Las versiones redistribuibles específicas de la arquitectura de ucrtbase.dll para la implementación local se encuentran en Windows SDK. De forma predeterminada, Visual Studio las instala en C:\Archivos de programa (x86)\Windows Kits\10\Redist\ucrt\DLLs\ en un subdirectorio específico de la arquitectura.  
  
 Si la aplicación se compila mediante una versión anterior de la biblioteca MFC, tendrá que redistribuir el archivo DLL de CRT correspondiente desde el directorio de los archivos redistribuibles. Por ejemplo, si la aplicación MFC se compila mediante el conjunto de herramientas de Visual Studio 2013 (vc120), debe redistribuir el archivo msvcr120.dll. También tendrá que redistribuir los archivos mfc`<version>`u.dll o mfc`<version>`.dll que coincidan.  
  
 Si vincula estáticamente la aplicación a MFC (es decir, si se especifica **Utilizar MFC en una biblioteca estática** en la pestaña **General** del cuadro de diálogo **Páginas de propiedades**), no es necesario redistribuir un archivo DLL de MFC. Sin embargo, aunque la vinculación estática puede funcionar para probar la implementación interna de las aplicaciones, se recomienda no utilizarla para redistribuir MFC. Para obtener más información sobre las estrategias recomendadas para implementar las bibliotecas de Visual C++, vea [Elegir un método de implementación](../ide/choosing-a-deployment-method.md).  
  
 Si en la aplicación se usan las clases MFC que implementan el control WebBrowser (por ejemplo, las clases [CHtmlView](../mfc/reference/chtmlview-class.md) o [CHtmlEditView](../mfc/reference/chtmleditview-class.md)), se recomienda instalar también la versión más actual de Microsoft Internet Explorer, de forma que el equipo de destino tenga los archivos de control comunes más recientes. (Como mínimo, se requiere Internet Explorer 4.0.) La información sobre cómo instalar los componentes de Internet Explorer se encuentra disponible en el artículo "Article 185375: How To Create a Single EXE Install of Internet Explorer"" en el sitio web de Soporte Microsoft.  
  
 Si en la aplicación se usan las clases de base de datos de MFC (como por ejemplo, [CRecordset](../mfc/reference/crecordset-class.md) y [CRecordView](../mfc/reference/crecordview-class.md)), tendrá que redistribuir ODBC y todos los controladores ODBC que se usen en la aplicación. Para obtener más información, vea [Redistribuir archivos de compatibilidad con bases de datos](../ide/redistributing-database-support-files.md).  
  
 Si la aplicación MFC utiliza controles de Windows Forms, deberá redistribuir mfcmifc80.dll con la aplicación. Este archivo DLL es un ensamblado .NET firmado y con nombre seguro que se puede redistribuir con una aplicación en la carpeta local de la aplicación o implementándolo en la caché global de ensamblados (GAC) mediante [Gacutil.exe (Herramienta Caché global de ensamblados)](/dotnet/framework/tools/gacutil-exe-gac-tool).  
  
 Si redistribuye una DLL de MFC, asegúrese de redistribuir la versión comercial, y no la de depuración. Las versiones de depuración de las DLL no son redistribuibles. Los nombres de las versiones de depuración de los archivos DLL de MFC finalizan con una "d", por ejemplo, Mfc140d.dll.  
  
 Se puede redistribuir MFC mediante VCRedist_*arquitectura*.exe, módulos de combinación que se instalan con Visual Studio, o bien mediante la implementación del archivo DLL de MFC en la misma carpeta que la aplicación. Para obtener más información sobre cómo redistribuir MFC, vea [Redistribuir archivos de Visual C++](../ide/redistributing-visual-cpp-files.md).  
  
## <a name="installation-of-localized-mfc-components"></a>Instalación de componentes de MFC localizados  
 Si decide localizar la aplicación instalando una localización DLL de MFC, debe utilizar los archivos redistribuibles de fusión mediante combinación (.msm). Por ejemplo, si quiere localizar la aplicación en un equipo x86, debe combinar Microsoft_VC`<version>`_MFCLOC_x86.msm en el paquete de instalación para un equipo x86.  
  
 Los archivos .msm redistribuibles contienen los archivos DLL que se utilizan para la localización. Hay un archivo DLL para cada lenguaje compatible. Durante el proceso de instalación se instalan estos archivos DLL en la carpeta %windir%\system32\ del equipo de destino.  
  
 Para obtener más información sobre cómo localizar las aplicaciones MFC, vea [TN057: Localización de componentes de MFC](../mfc/tn057-localization-of-mfc-components.md) y también el [Article 208983: How to Using MFC LOC DLLs](http://go.microsoft.com/fwlink/p/?linkid=198025) (Artículo 208983: Cómo usar archivos DLL de localización de MFC) en el sitio web de Soporte de Microsoft.  
  
 Puede redistribuir archivos DLL de localización de MFC si implementa el archivo DLL de MFC en la carpeta local de la aplicación. Para obtener más información sobre cómo redistribuir bibliotecas de Visual C++, vea [Redistribuir archivos de Visual C++](../ide/redistributing-visual-cpp-files.md).  
  
## <a name="see-also"></a>Vea también  
 [Redistribuir archivos de Visual C++](../ide/redistributing-visual-cpp-files.md)