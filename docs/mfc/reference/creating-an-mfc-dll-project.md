---
title: Crear un proyecto DLL de MFC | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.mfcdll.project
dev_langs:
- C++
helpviewer_keywords:
- MFC DLLs [C++], creating projects
- DLLs [C++], MFC
- projects [C++], creating
- DLLs [C++], creating
ms.assetid: 05540b93-4781-4a90-aadf-55158313f5b2
caps.latest.revision: 13
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: c403d1351c43e043fd3048d342dafcf069951446
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="creating-an-mfc-dll-project"></a>Crear un proyecto DLL de MFC
Un archivo DLL de MFC es un archivo binario que actúa como una biblioteca compartida de funciones que pueden utilizar simultáneamente varias aplicaciones. La forma más fácil de crear un proyecto DLL de MFC es utilizar el Asistente para archivos DLL de MFC.  
  
> [!NOTE]
>  Las características del IDE pueden depender de la edición o configuración activa, y ser diferentes de las que se describen en la Ayuda. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, vea [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-an-mfc-dll-project-using-the-mfc-dll-wizard"></a>Para crear un proyecto DLL de MFC mediante el Asistente para archivos DLL de MFC  
  
1.  Siga las instrucciones del tema de Ayuda [crear un proyecto con un Asistente para aplicaciones de Visual C++](../../ide/creating-desktop-projects-by-using-application-wizards.md).  
  
 **Nota** en el **nuevo proyecto** cuadro de diálogo, seleccione el `MFC DLL` icono en el panel Plantillas para abrir el Asistente para archivos DLL de MFC.  
  
1.  Defina la configuración de la aplicación mediante el [configuración de la aplicación](../../mfc/reference/application-settings-mfc-dll-wizard.md) página de la [Asistente para archivos DLL de MFC](../../mfc/reference/mfc-dll-wizard.md).  
  
    > [!NOTE]
    >  Omita este paso para mantener la configuración predeterminada del asistente.  
  
2.  Haga clic en **finalizar** para cerrar el asistente y abrir el proyecto nuevo en **el Explorador de soluciones**.  
  
 Cuando haya creado el proyecto, podrá ver los archivos creados en el Explorador de soluciones. Para obtener más información sobre los archivos que crea el asistente para el proyecto, vea el archivo Readme.txt generado por el proyecto. Para obtener más información acerca de los tipos de archivo, consulte [tipos de archivo creados para proyectos de Visual C++](../../ide/file-types-created-for-visual-cpp-projects.md).  
  
## <a name="see-also"></a>Vea también  
 [Tipos de proyecto de Visual C++](http://msdn.microsoft.com/library/912b4ba2-7719-43d5-b087-db33e3f9329a)   
 [Agregar funcionalidad con los asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Páginas de propiedades](../../ide/property-pages-visual-cpp.md)   
 [Implementación de aplicaciones](http://msdn.microsoft.com/en-us/4ff8881d-0daf-47e7-bfe7-774c625031b4)


