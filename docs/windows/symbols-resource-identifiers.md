---
title: "Symbols: Resource Identifiers | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.symbol.identifiers"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "symbols, resource identifiers"
  - "symbols, creating"
  - "resource symbols"
  - "symbols, editing"
  - "resource editors, resource symbols"
ms.assetid: 8fccc09a-0237-4a65-b9c4-57d60c59e324
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Symbols: Resource Identifiers
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un símbolo es un identificador de recurso \(id.\) que consta de dos partes: una cadena de texto \(nombre del símbolo\) asignada a un valor entero \(valor del símbolo\). Por ejemplo:  
  
```  
IDC_EDITNAME = 5100  
```  
  
 Los nombres de símbolos a menudo se denominan identificadores.  
  
 Los símbolos ofrecen un medio descriptivo para hacer referencia a los recursos y objetos de interfaz de usuario, tanto en el código fuente como mientras trabaja con ellos en los editores de recursos. Puede ver y manipular símbolos en un lugar cómodo mediante el [cuadro de diálogo Símbolos de recursos](../windows/viewing-resource-symbols.md).  
  
 Cuando crea un nuevo recurso o un objeto de recurso, los [editores de recursos](../mfc/resource-editors.md) ofrecen un nombre predeterminado para el recurso, por ejemplo, `IDC_RADIO1`, y le asignan un valor. La definición de nombre y valor se almacena en el archivo Resource.h.  
  
> [!NOTE]
>  Cuando se copian recursos u objetos de recursos de un archivo .rc a otro, Visual C\+\+ puede cambiar el valor del símbolo del recurso transferido, o el nombre del símbolo y el valor, para evitar conflictos con nombres de símbolos o valores del archivo existente.  
  
 Conforme aumenta el tamaño y la sofisticación de su aplicación, lo hacen también su número de recursos y símbolos. El seguimiento de grandes números de símbolos dispersos en varios archivos puede resultar difícil. El [cuadro de diálogo Símbolos de recursos](../windows/resource-symbols-dialog-box.md) simplifica la administración de símbolos mediante una herramienta central que permite:  
  
-   [Ver símbolos de recursos](../windows/viewing-resource-symbols.md)  
  
-   [Crear nuevos símbolos](../windows/creating-new-symbols.md)  
  
-   [Cambiar símbolos sin asignar](../Topic/Changing%20Unassigned%20Symbols.md)  
  
-   [Eliminar símbolos sin asignar](../windows/deleting-unassigned-symbols.md)  
  
-   [Abrir el Editor de recursos para un símbolo determinado](../Topic/Opening%20the%20Resource%20Editor%20for%20a%20Given%20Symbol.md)  
  
-   [Cambiar un símbolo o el nombre de un símbolo \(id.\)](../windows/changing-a-symbol-or-symbol-name-id.md)  
  
-   [Cambiar el valor numérico de un símbolo](../windows/changing-a-symbol-s-numeric-value.md)  
  
-   [Cambiar los nombres de los archivos de encabezado de símbolos](../windows/changing-the-names-of-symbol-header-files.md)  
  
-   [Incluir símbolos compartidos \(de sólo lectura\) o calculados](../windows/including-shared-read-only-or-calculated-symbols.md)  
  
-   [Ver id. de de símbolos predefinidos](../windows/predefined-symbol-ids.md)  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, obtener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Tutorial: adaptar Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
## Requisitos  
 Win32  
  
## Vea también  
 [How to: Search for Symbols in Resources](../windows/how-to-search-for-symbols-in-resources.md)   
 [Resource Editors](../mfc/resource-editors.md)   
 [Resource Files](../mfc/resource-files-visual-studio.md)