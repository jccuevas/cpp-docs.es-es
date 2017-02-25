---
title: "How to: Change the Language or Condition of a Resource While Copying | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.resvw.resource.changing"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Language property"
  - "condition property of resource"
ms.assetid: 8f622ab0-bac2-468f-ae70-78911afc4759
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# How to: Change the Language or Condition of a Resource While Copying
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Al copiar un recurso, puede cambiar sus propiedades de idioma, condición o ambas.  
  
-   El idioma del recurso identifica exactamente eso, el idioma del recurso.  [FindResource](http://msdn.microsoft.com/library/windows/desktop/ms648042) usa esta característica para ayudar a identificar el recurso que busca.  \(Sin embargo, los recursos pueden tener diferencias para cada idioma que no estén relacionados con texto, por ejemplo, aceleradores que solo funcionen en teclados japoneses, un mapa de bits que solo sea adecuado para compilaciones localizadas en chino, etc.\).  
  
-   La condición de un recurso es un símbolo definido que identifica una condición en la que esta copia concreta del recurso se va a utilizar.  
  
 El idioma y la condición de un recurso se muestran entre paréntesis después del nombre del recurso en la ventana del área de trabajo.  En este ejemplo, el recurso denominado IDD\_AboutBox tienen finés como idioma y XX33 como condición.  
  
```  
IDD_AboutBox (Finnish – XX33)  
```  
  
### Para copiar un recurso existente y cambiar su idioma o su condición  
  
1.  En el archivo .rc o en la ventana [Vista de recursos](../windows/resource-view-window.md), haga clic en el recurso que desea copiar.  
  
2.  Elija **Insertar copia** en el menú contextual.  
  
3.  En el cuadro de diálogo **Insertar copia de recursos**:  
  
    -   En el cuadro de lista **Idioma**, seleccione el idioma.  
  
    -   En el cuadro **Condición**, escriba la condición.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 Requisitos  
  
 Win32  
  
## Vea también  
 [How to: Copy Resources](../windows/how-to-copy-resources.md)   
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Resource Editors](../mfc/resource-editors.md)