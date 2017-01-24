---
title: "S&#237;mbolos de recursos (Cuadro de di&#225;logo) | Microsoft Docs"
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
  - "vc.editors.resourcesymbols"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Nuevo símbolo (cuadro de diálogo)"
  - "Símbolos de recursos (cuadro de diálogo)"
  - "Cambiar símbolo (cuadro de diálogo)"
ms.assetid: 9706cde3-1f48-4fcd-bedb-2b03b455e3c1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# S&#237;mbolos de recursos (Cuadro de di&#225;logo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El cuadro de diálogo **Símbolos de recursos** permite agregar símbolos de recursos nuevos, cambiar los símbolos que se muestran o saltar a la ubicación del código fuente donde se usa un símbolo.  
  
 **Name**  
 Muestra el nombre del símbolo.  Para obtener más información, consulte [Restricciones de los nombres de símbolo](../windows/symbol-name-restrictions.md).  
  
 **Valor**  
 Muestra el valor numérico del símbolo.  Para obtener más información, consulte [Restricciones de los valores de símbolo](../Topic/Symbol%20Value%20Restrictions.md).  
  
 **En uso**  
 Si se selecciona, especifica si el símbolo se usa en uno o varios recursos.  El o los recursos se enumeran en el cuadro Usado por.  
  
 **Mostrar símbolos de solo lectura**  
 Si se selecciona, muestra los recursos de solo lectura.  De forma predeterminada, el cuadro de diálogo Símbolos de recursos solo muestra los recursos modificables en el archivo de script de recursos. Si selecciona esta opción, los recursos modificables aparecen en negrita y, los de solo lectura, en texto sin formato.  
  
 **Usado por**  
 Muestra el o los recursos que usan el símbolo seleccionado en la lista de símbolos.  Si desea mover el editor para un recurso determinado, seleccione este recurso en el cuadro **Usado por** y haga clic en **Ver uso**.  Para obtener más información, consulte [Abrir el Editor de recursos para un símbolo determinado](../Topic/Opening%20the%20Resource%20Editor%20for%20a%20Given%20Symbol.md).  
  
 **Nuevo**  
 Abre el cuadro de diálogo Nuevo símbolo, que permite definir el nombre y, si es necesario, un valor para el nuevo identificador de recurso simbólico.  Para obtener más información, consulte [Crear nuevos símbolos](../windows/creating-new-symbols.md).  
  
 **Cambiar**  
 Abre el cuadro de diálogo Cambiar símbolo, que permite cambiar el nombre o el valor de un símbolo.  Si el símbolo es para un control o un recurso en uso, solo se puede cambiar desde el editor de recursos correspondiente.  Para obtener más información, consulte [Cambiar símbolos sin asignar](../Topic/Changing%20Unassigned%20Symbols.md).  
  
 **Ver uso**  
 Abre el recurso que contiene el símbolo en el editor de recursos correspondiente.  Para obtener más información, consulte [Abrir el Editor de recursos para un símbolo determinado](../Topic/Opening%20the%20Resource%20Editor%20for%20a%20Given%20Symbol.md).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener más información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, consulte [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
## Requisitos  
 Win32  
  
## Vea también  
 [Viewing Resource Symbols](../windows/viewing-resource-symbols.md)