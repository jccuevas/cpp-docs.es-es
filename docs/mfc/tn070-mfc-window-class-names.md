---
title: "TN070: Nombres de clases de ventana | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.classes"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "TN070"
  - "nombres de clases de ventana"
ms.assetid: 90617912-dd58-4a7c-9082-ced71736d7cd
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# TN070: Nombres de clases de ventana
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea.  Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos.  Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Las ventanas de MFC utilizan un nombre de clase creado dinámicamente que refleje las características de la ventana.  MFC generará nombres de clase dinámicamente para las ventanas, las vistas, las ventanas emergentes de cuadro generadas por la aplicación.  Los cuadros de diálogo y los controles generados por una aplicación MFC tienen el nombre Windows\- proporcionado para la clase de ventana en cuestión.  
  
 Puede reemplazar el nombre de clase dinámicamente proporcionado registrando dispone de la clase de ventana y usándola en un reemplazo de [PreCreateWindow](../Topic/CWnd::PreCreateWindow.md).  Los nombres de clase MFC\- proporcionados cupieron uno de los dos formularios de siguiente:  
  
```  
Afx:%x:%x  
Afx:%x:%x:%x:%x:%x  
```  
  
 Los dígitos hexadecimales que reemplazan los caracteres de `%x` se completan de datos de la estructura de [Clase WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) .  MFC utiliza esta técnica de modo que varias clases de C\+\+ que requieren las estructuras idénticas de **WNDCLASS** pueden compartir la misma clase de ventana registrada.  A diferencia de la mayoría de las aplicaciones Win32 simples, las aplicaciones MFC sólo tienen un **WNDPROC**, por lo que es fácil compartir las estructuras de **WNDCLASS** para ahorrar tiempo y memoria.  Los valores reemplazables por caracteres de `%x` mostrados anteriormente son los siguientes:  
  
-   **WNDCLASS.hInstance**  
  
-   **WNDCLASS.style**  
  
-   **WNDCLASS.hCursor**  
  
-   **WNDCLASS.hbrBackground**  
  
-   **WNDCLASS.hIcon**  
  
 Se utiliza el primer formulario \(`Afx:%x:%x`\) cuando **hCursor**, **hbrBackground**, y **hIcon** son todas **nulo**.  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)   
 [TN020: Convenciones de nomenclatura y numeración de identificadores](../mfc/tn020-id-naming-and-numbering-conventions.md)