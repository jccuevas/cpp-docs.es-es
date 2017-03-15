---
title: "Redistribuir la biblioteca MFC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC, redistribuir"
  - "redistribuir la biblioteca MFC"
ms.assetid: 72714ce1-385e-4c1c-afa5-96b03e873866
caps.latest.revision: 32
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 29
---
# Redistribuir la biblioteca MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si vincula dinámicamente la aplicación a la biblioteca MFC, deberá redistribuir Msvcr100.dll porque todos los archivos DLL de MFC usan la versión compartida de la biblioteca en tiempo de ejecución de C \(CRT\).  También tiene que redistribuir Mfc100u.dll o Mfc100.dll.  
  
 Si vincula estáticamente la aplicación a MFC \(es decir, si se especifica **Utilizar MFC en una biblioteca estática** en la pestaña **General** del cuadro de diálogo **Páginas de propiedades**\), no es necesario redistribuir Mfc100u.dll o Mfc100.dll.  Sin embargo, aunque la vinculación estática puede funcionar para probar la implementación interna de las aplicaciones, se recomienda no utilizarla para redistribuir MFC.  Para obtener más información sobre las estrategias recomendadas para implementar las bibliotecas de Visual C\+\+, vea [Elegir un método de implementación](../ide/choosing-a-deployment-method.md).  
  
 Si la aplicación utiliza las clases MFC que implementan el control ExploradorWeb \(por ejemplo, [Clase CHtmlView](../mfc/reference/chtmlview-class.md) o [CHtmlEditView Class](../mfc/reference/chtmleditview-class.md)\), es recomendable que también instalar la versión más actual de Microsoft Internet Explorer, de forma que el equipo de destino tenga la mayoría de los archivos actuales de control común. \(Como mínimo, se requiere Internet Explorer 4.0.\) La información sobre cómo instalar los componentes de Internet Explorer se encuentra disponible en el artículo "Article 185375: How To Create a Single EXE Install of Internet Explorer"" en el sitio web de Soporte Microsoft.  
  
 Si la aplicación utiliza clases de base de datos de MFC \(como por ejemplo, [CRecordset Class](../mfc/reference/crecordset-class.md) y [CRecordView Class](../mfc/reference/crecordview-class.md)\), deberá redistribuir ODBC y cualquier controlador ODBC utilizado por la aplicación.  Para obtener más información, vea [Redistribuir archivos de compatibilidad con bases de datos](../ide/redistributing-database-support-files.md).  
  
 Si la aplicación MFC utiliza controles de Windows Forms, deberá redistribuir mfcmifc80.dll con la aplicación.  Esta DLL es un ensamblado .NET firmado y con nombre seguro que se puede redistribuir con una aplicación en la carpeta local de la aplicación o implementándolo en Caché global de ensamblados \(GAC\) mediante [Gacutil.exe \(Global Assembly Cache Tool\)](../Topic/Gacutil.exe%20\(Global%20Assembly%20Cache%20Tool\).md).  
  
 Si redistribuye una DLL de MFC, asegúrese de redistribuir la versión comercial, y no la de depuración.  Las versiones de depuración de las DLL no son redistribuibles.  Los nombres de las versiones de depuración de los archivos DLL de MFC finalizan con una "d", por ejemplo, Mfc100d.dll.  
  
 Si modifica el código fuente de MFC y después recompila el archivo DLL de MFC, deberá cambiar el nombre del archivo DLL de MFC modificado para que no entre en conflicto con el archivo DLL de MFC incluido en Visual Studio.  Se recomienda no recompilar o cambiar el nombre del archivo DLL de MFC.  Para obtener más información, vea la Nota técnica 33 de MFC.  
  
 Puede redistribuir MFC mediante VCRedist\_*architecture*.exe, módulos de combinación que se instalan con Visual Studio, o mediante la implementación del archivo DLL de MFC en la misma carpeta que la aplicación.  Para obtener más información sobre cómo redistribuir MFC, vea [Redistribuir archivos de Visual C\+\+](../ide/redistributing-visual-cpp-files.md).  
  
## Instalación de componentes de MFC localizados  
 Si decide localizar la aplicación instalando una localización DLL de MFC, debe utilizar los archivos redistribuibles de combinación \(.msm\).  Por ejemplo, si desea localizar la aplicación en un equipo de x86, debe combinar Microsoft\_VC100\_MFCLOC\_x86.msm en el paquete de instalación para un equipo x86.  
  
 Los archivos .msm redistribuibles contienen los archivos DLL que se utilizan para la localización.  Hay un archivo DLL para cada lenguaje compatible.  Durante el proceso de instalación se instalan estos archivos DLL en la carpeta %windir%\\system32\\ del equipo de destino.  
  
 Para obtener más información sobre cómo localizar aplicaciones MFC, vea [TN057: Localización de componentes de MFC](../mfc/tn057-localization-of-mfc-components.md) y también el [Artículo 208983: Utilizar archivos DLL de localización de MFC](http://go.microsoft.com/fwlink/?LinkId=198025) en el sitio web de Soporte de Microsoft.  
  
 Puede redistribuir archivos DLL de localización de MFC si implementa el archivo DLL de MFC en la carpeta local de la aplicación.  Para obtener más información sobre cómo redistribuir las bibliotecas de Visual C\+\+, vea [Redistribuir archivos de Visual C\+\+](../ide/redistributing-visual-cpp-files.md).  
  
## Vea también  
 [Redistribuir archivos de Visual C\+\+](../ide/redistributing-visual-cpp-files.md)