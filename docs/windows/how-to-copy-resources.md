---
title: "How to: Copy Resources | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.resvw.resource.copying"
  - "vs.resvw.resource.copying"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "resources [Visual Studio], moving between files"
  - "resources [Visual Studio], copying"
  - "resource files, copying or moving resources between"
  - "resource files, tiling"
  - ".rc files, copying resources between"
  - "rc files, copying resources between"
ms.assetid: 65f523e8-017f-4fc6-82d1-083c56d9131f
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# How to: Copy Resources
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede copiar recursos de un archivo a otro sin cambiarlos; y también puede [cambiar el idioma o la condición de un recurso mientras lo copia](../windows/how-to-change-the-language-or-condition-of-a-resource-while-copying.md).  
  
 Copiar recursos de un archivo de recursos o ejecutable ya existente al archivo de recursos actual es muy fácil:  abra los dos archivos que contienen recursos a la vez y arrastre elementos de uno al otro o, simplemente, copie y pegue entre ambos.  Este método funciona tanto con archivos de script de recursos \(.rc\) y archivos de plantillas de recursos \(.rct\), como con archivos ejecutables \(.exe\).  
  
> [!NOTE]
>  Visual C\+\+ incluye archivos de recursos de ejemplo que podrá utilizar para sus propias aplicaciones.  Para obtener más información, vea [CLIPART: recursos comunes](http://msdn.microsoft.com/es-es/9bac2891-b6b3-49ec-a287-cec850c707e0).  
  
 El método de arrastrar y colocar puede utilizarse entre archivos .rc que estén abiertos [fuera del proyecto](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).  
  
### Para copiar recursos entre archivos mediante el método de arrastrar y colocar  
  
1.  Abra ambos archivos de recursos en modo independiente. Para obtener más información, vea [Ver recursos en un archivo de script de recursos fuera de un proyecto](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).  Por ejemplo, abra Source1.rc y Source2.rc.  
  
2.  En el primer archivo .rc, haga clic en el recurso que desee copiar.  Por ejemplo, en Source1.rc, haga clic en IDD\_DIALOG1.  
  
3.  Mantenga presionada la tecla CTRL y arrastre el recurso al segundo archivo .rc.  Por ejemplo, arrastre IDD\_DIALOG1 de Source1.rc a Source2.rc.  
  
    > [!NOTE]
    >  Si arrastra el recurso sin mantener presionada la tecla CTRL, se moverá en lugar de copiarse.  
  
### Para copiar recursos con copiar y pegar  
  
1.  Abra ambos archivos de recursos en modo independiente. Para obtener más información, vea [Ver recursos en un archivo de script de recursos fuera de un proyecto](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).  Por ejemplo, abra Source1.rc y Source2.rc.  
  
2.  En el archivo de código fuente desde el que desee copiar el recurso \(por ejemplo, Source1.rc\), haga clic con el botón secundario en el recurso y elija **Copiar** en el menú contextual.  
  
3.  Haga clic con el botón secundario en el archivo de recursos en el que desee pegar el recurso \(por ejemplo, Source2.rc\).  Elija **Pegar** en el menú contextual.  
  
    > [!NOTE]
    >  No se pueden realizar las acciones de arrastrar y colocar, copiar, cortar o pegar entre archivos de recursos del proyecto \(Vista de recursos\) y archivos .rc independientes \(abiertos en ventanas de documento\).  En versiones anteriores del producto, sin embargo, sí era posible.  
  
    > [!NOTE]
    >  Para evitar conflictos entre nombres o valores de símbolos en el archivo existente, puede que Visual C\+\+ cambie el valor o el nombre de símbolo del recurso transferido cuando lo copie al nuevo archivo.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 Requisitos  
  
 Win32  
  
## Vea también  
 [How to: Open a Resource Script File Outside of a Project \(Standalone\)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)   
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Resource Editors](../mfc/resource-editors.md)