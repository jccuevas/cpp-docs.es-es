---
title: "Declarar una variable basada en una clase de control nueva | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.classes.control.variable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases [C++], declarar variables basadas en"
  - "clases de controles, variables"
  - "variables, clases de controles"
ms.assetid: 5722dc38-c0eb-40bd-93da-67a808140d03
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Declarar una variable basada en una clase de control nueva
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una vez se haya creado una nueva clase de control MFC, se puede declarar una variable a partir de ella.  Para proporcionar un contexto para la nueva variable, se debe abrir el editor de cuadros de diálogo y editar el cuadro de diálogo donde se desea utilizar el control reutilizable.  Igualmente, el cuadro de diálogo debe contar con una clase asociada a él.  Para obtener más información sobre cómo utilizar el editor de cuadros de diálogo, vea [Editor de cuadros de diálogo](../../mfc/dialog-editor.md).  
  
### Para declarar una variable basada en una clase reutilizable  
  
1.  Al editar el cuadro de diálogo, arrastre un control del mismo tipo que la clase base del nuevo control desde la barra de herramientas Controles al cuadro de diálogo.  
  
2.  Coloque el puntero del mouse  sobre el control arrastrado.  
  
3.  Mantenga presionada la tecla CTRL y haga doble clic en el control.  
  
     Aparecerá el cuadro de diálogo [Asistente para agregar variables miembro](../../ide/add-member-variable-wizard.md).  
  
4.  En el cuadro **Acceso**, seleccione el acceso correcto para el control.  
  
5.  Haga clic en la casilla **Variable del control**.  
  
6.  En el cuadro **Nombre de variable**, escriba un nombre.  
  
7.  En **Categoría**, haga clic en **Control**.  
  
8.  En la lista **Id. de control**, elija el control que agregó.  La lista **Tipo de variable** debe mostrar el tipo de variable correcto, y el cuadro **Tipo de control** debe mostrar el tipo de control adecuado.  
  
9. En el cuadro **Comentario**, agregue cualquier comentario que desee que aparezca en el código.  
  
10. Haga clic en **Aceptar**.  
  
## Vea también  
 [Asignar mensajes a funciones](../../mfc/reference/mapping-messages-to-functions.md)   
 [Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Agregar una clase](../../ide/adding-a-class-visual-cpp.md)   
 [Agregar una función miembro](../../ide/adding-a-member-function-visual-cpp.md)   
 [Agregar una variable miembro](../../ide/adding-a-member-variable-visual-cpp.md)   
 [Reemplazar una función virtual](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Controlador de mensajes de MFC](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [Explorar la estructura de clases](../../ide/navigating-the-class-structure-visual-cpp.md)