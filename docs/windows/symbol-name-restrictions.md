---
title: "Symbol Name Restrictions | Microsoft Docs"
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
  - "vc.editors.symbol.restrictions.name"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "symbol names"
  - "symbols, names"
  - "restrictions, symbol names"
ms.assetid: 4ae7f695-ca86-4f4b-989a-fe6f89650ff7
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Symbol Name Restrictions
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las restricciones en los nombres de símbolos son las siguientes:  
  
-   Todos los [símbolos](../mfc/symbols-resource-identifiers.md) han de ser únicos dentro del ámbito de la aplicación.  Esto evita conflictos de definiciones de símbolos en los archivos de encabezado.  
  
-   Los caracteres válidos en un nombre de símbolo son A\-z, a\-z, 0\-9 y caracteres de subrayado \(\_\).  
  
-   Los nombres de símbolo no pueden empezar por un número y se limitan a 247 caracteres.  
  
-   Los nombres de símbolo no pueden contener espacios.  
  
-   Los nombres de símbolo no distinguen entre mayúsculas y minúsculas, pero se conservan las mayúsculas o minúsculas de la primera definición de símbolos.  El compilador\/editor de recursos y los programas de C\+\+  usan el archivo de encabezado que define los símbolos para hacer referencia a los recursos definidos en un archivo de recursos.  Cuando dos nombres de símbolo difieren únicamente en sus mayúsculas o minúsculas, el programa de C\+\+ verá dos símbolos distintos, mientras que el compilador\/editor de recursos verá dos nombres se remiten al mismo símbolo.  
  
    > [!NOTE]
    >  Si no respeta el esquema de nombre de símbolo estándar \(ID\*\_\[palabra clave\]\) descrito aquí y el nombre del símbolo resulta ser el mismo que una palabra clave conocida por el compilador de script de recursos, cuando trate de generar el archivo de script de recursos, se producirá un error aparentemente aleatorio difícil de diagnosticar.  Para evitar esto, aténgase al esquema de nomenclatura estándar.  
  
 Los nombres de símbolo tienen prefijos descriptivos que indican el tipo de recurso u objeto que representan.  Estos prefijos descriptivos comienzan por el identificador de combinación de texto.  La biblioteca MFC \(Microsoft Foundation Class\) usa las convenciones de nomenclatura de símbolo recogidas en la siguiente tabla.  
  
|Categoría|Prefijo|Usar|  
|---------------|-------------|----------|  
|Recursos|IDR\_ IDD\_ IDC\_ IDI\_ IDB\_|Acelerador o menú \(y recursos asociados o personalizados\) Cuadro de diálogo Cursor Icono Mapa de bits|  
|Elementos de menú|ID\_|Elemento de menú|  
|Comandos|ID\_|Comando|  
|Controles y ventanas secundarias|IDC\_|Control|  
|Cadenas|IDS\_|Cadena en la tabla de cadenas|  
|MFC|AFX\_|Reservado para símbolos de MFC predefinidos|  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Vea el [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md) para obtener más información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo tener acceso a los recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades.  
  
## Requisitos  
 Win32  
  
## Vea también  
 [Changing a Symbol or Symbol Name \(ID\)](../windows/changing-a-symbol-or-symbol-name-id.md)   
 [Symbol Value Restrictions](../Topic/Symbol%20Value%20Restrictions.md)   
 [Predefined Symbol IDs](../windows/predefined-symbol-ids.md)