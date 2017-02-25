---
title: "Establecer las propiedades de los aceleradores | Microsoft Docs"
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
  - "propiedades de acelerador"
  - "propiedades [C++], propiedades de Acelerador"
  - "Type (propiedad)"
  - "Key (propiedad)"
  - "Modifier (propiedad)"
ms.assetid: 0fce9156-3025-4e18-b034-e219a4c65812
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Establecer las propiedades de los aceleradores
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En Visual C++. NET, puede establecer propiedades de acelerador el [ventana propiedades](../Topic/Properties%20Window.md) en cualquier momento. También puede utilizar el Editor de aceleradores para modificar las propiedades de acelerador de la tabla de aceleradores. Los cambios realizados mediante la ventana Propiedades o el Editor de aceleradores tienen el mismo resultado: las modificaciones se reflejan inmediatamente en la tabla de aceleradores.  
  
 Hay tres propiedades para cada acelerador [ID](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/3487f185-de96-4b1d-87db-034a52223160/locales/en-US):  
  
-   El [Modifier (propiedad)](../windows/accelerator-modifier-property.md) establece el control de combinaciones de teclas para el acelerador.  
  
    > [!NOTE]
    >  En la ventana Propiedades, esta propiedad aparece como tres propiedades booleanas independientes que pueden controlarse de forma independiente: Alt, Ctrl y Mayús.  
  
-   El [propiedad clave](../Topic/Accelerator%20Key%20Property.md) establece la clave real que se usará como el acelerador.  
  
-   El [tipo de propiedad](../windows/accelerator-type-property.md) determina si la clave se interpreta como virtual (VIRTKEY) o ASCII/ANSI.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework* . Para información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
## <a name="requirements"></a>Requisitos  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Teclas de aceleración predefinidas](../windows/predefined-accelerator-keys.md)   
 [Editores de recursos](../mfc/resource-editors.md)   
 [Editor de aceleradores](../mfc/accelerator-editor.md)