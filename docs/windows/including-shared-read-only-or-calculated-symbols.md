---
title: "Including Shared (Read-Only) or Calculated Symbols | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.symbol.shared.calculated"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "symbols, read-only"
  - "symbols, shared"
  - "symbols, calculated"
  - "read-only symbols"
  - "symbol directives"
  - "calculated symbols"
  - "shared symbols"
ms.assetid: 32b77faf-a066-4371-a072-9a5b84c0766d
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Including Shared (Read-Only) or Calculated Symbols
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La primera vez que el entorno de desarrollo lee un archivo de recursos creado por otra aplicación, marca todos los archivos de encabezado incluidos como de solo lectura.  Posteriormente, puede usar el [Cuadro de diálogo Archivos de inclusión de recursos](../windows/resource-includes-dialog-box.md) para agregar archivos adicionales de encabezado de símbolos de solo lectura.  
  
 Tal vez le interese usar definiciones de símbolos de solo lectura para los archivos de símbolos que desea compartir entre varios proyectos.  
  
 También puede usar los archivos de símbolos incluidos cuando dispone de recursos existentes con definiciones de símbolos que usan expresiones en lugar de enteros sencillos para definir el valor de símbolo.  Por ejemplo:  
  
```  
#define   IDC_CONTROL1 2100  
#define   IDC_CONTROL2 (IDC_CONTROL1+1)  
```  
  
 El entorno interpreta correctamente estos símbolos calculados siempre y cuando:  
  
-   Los símbolos calculados se coloquen en un archivo de símbolos de solo lectura.  
  
-   El archivo de recursos contenga recursos a los que ya están asignados estos símbolos calculados.  
  
-   Se espere una expresión numérica.  
  
> [!NOTE]
>  Si se espera una cadena o una expresión numérica, la expresión no se evalúa.  
  
### Para incluir símbolos compartidos \(de solo lectura\) en el archivo de recursos  
  
1.  En [Vista de recursos](../windows/resource-view-window.md), haga clic con el botón derecho en el archivo .rc y elija [Archivos de inclusión de recursos](../windows/resource-includes-dialog-box.md) en el menú contextual.  
  
    > [!NOTE]
    >  Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
2.  En el cuadro **Directivas de símbolos de solo lectura**, use la directiva de compilador **\#include** para especificar el archivo donde desea que se conserven los símbolos de solo lectura.  
  
     No llame al archivo Resource.h, ya que es el nombre de archivo que suele usar el archivo de encabezado de símbolos principal.  
  
    > [!NOTE]
    >  **Importante** Lo que escriba en el cuadro Directivas de símbolos de solo lectura se incluye en el archivo de recursos exactamente como lo escriba.  Asegúrese de que lo que escribe no contiene errores de sintaxis o de ortografía.  
  
     Use el cuadro **Directivas de símbolos de solo lectura** para incluir archivos solamente con las definiciones de símbolos.  No incluya definiciones de recursos; en caso contrario, se crearán definiciones de recursos duplicadas cuando se guarde el archivo.  
  
3.  Coloque los símbolos en el archivo especificado.  
  
     Los símbolos de los archivos incluidos de esta manera se evalúan cada vez que abra el archivo de recursos, pero no se reemplazan en el disco cuando guarde el archivo.  
  
4.  Haga clic en **Aceptar**.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener más información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, consulte [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 Requisitos  
  
 Win32  
  
## Vea también  
 [Symbol Name Restrictions](../windows/symbol-name-restrictions.md)   
 [Symbol Value Restrictions](../Topic/Symbol%20Value%20Restrictions.md)   
 [Predefined Symbol IDs](../windows/predefined-symbol-ids.md)   
 [Symbols: Resource Identifiers](../mfc/symbols-resource-identifiers.md)