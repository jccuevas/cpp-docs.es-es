---
title: "Intercambio de datos de cuadro de di&#225;logo | Microsoft Docs"
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
  - "cancelar el intercambio de datos"
  - "capturar la entrada del usuario"
  - "CDataExchange (clase), utilizar DDX"
  - "DDX (intercambio de datos de cuadros de diálogo), cancelar"
  - "DDX (intercambio de datos de cuadros de diálogo), mecanismo de intercambio de datos"
  - "datos del cuadro de diálogo"
  - "datos del cuadro de diálogo, recuperar"
  - "cuadros de diálogo, intercambio de datos"
  - "cuadros de diálogo, inicializar"
  - "cuadros de diálogo, recuperar los datos proporcionados por el usuario mediante DDX"
  - "DoDataExchange (método)"
  - "inicializar cuadros de diálogo"
  - "recuperar datos del cuadro de diálogo"
  - "transferir datos del cuadro de diálogo"
  - "UpdateData (método)"
  - "datos proporcionados por el usuario, recuperar de los cuadros de diálogo de MFC"
ms.assetid: 4675f63b-41d2-45ed-b6c3-235ad8ab924b
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Intercambio de datos de cuadro de di&#225;logo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si utiliza el mecanismo de DDX, establezca los valores iniciales de las variables miembro del objeto de cuadro de diálogo, normalmente en el controlador de `OnInitDialog` o el constructor del diálogo.  Inmediatamente antes de que se muestre el diálogo, el mecanismo de DDX de marco transfiere los valores de las variables miembros a los controles en el cuadro de diálogo, donde aparecen cuando el cuadro de diálogo propio aparece en respuesta a `DoModal` o a **crear**.  La implementación predeterminada de `OnInitDialog` en `CDialog` llama a la función miembro de `UpdateData` de la clase `CWnd` para inicializar los controles en el cuadro de diálogo.  
  
 El mismo mecanismo transfiere los valores de los controles a las variables miembro cuando el usuario hace clic en el botón ACEPTAR \(o siempre que llame a la función miembro de `UpdateData` con el argumento **VERDADERO**\).  El mecanismo de validación de datos de diálogo valida cualquier elemento de datos que especificó reglas de validación.  
  
 La ilustración siguiente muestra diálogo intercambio de datos.  
  
 ![Intercambio de datos de cuadro de diálogo](../mfc/media/vc379d1.png "vc379D1")  
Intercambio de datos de cuadro de diálogo  
  
 `UpdateData` funciona en ambas direcciones, especificado por el parámetro de **bool** pasa a.  Para realizar el intercambio, `UpdateData` coloca un objeto de `CDataExchange` y llama al reemplazo de la clase de diálogo de la función miembro de `CDialog``DoDataExchange` .  `DoDataExchange` toma un argumento de `CDataExchange`escrito.  El objeto de `CDataExchange` pasado a `UpdateData` representa el contexto de intercambio, definir información como la dirección de intercambio.  
  
 Cuando se \(o un asistente para código\) reemplaza `DoDataExchange`, especifica una llamada a una función de DDX por el miembro de datos \(control\).  Cada función de DDX conocidos para intercambiar los datos en ambas direcciones en función del contexto proporcionado por el argumento de `CDataExchange` pasado a `DoDataExchange` por `UpdateData`.  
  
 MFC proporciona muchas funciones DDX para los diferentes tipos de intercambio.  El ejemplo siguiente se muestra una invalidación de `DoDataExchange` en la que se llama dos funciones DDX y una función de DDV:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#49](../mfc/codesnippet/CPP/dialog-data-exchange_1.cpp)]  
  
 Las líneas de `DDX_` y de `DDV_` son un mapa de datos.  El ejemplo DDX y las funciones de DDV mostradas son para un control checkbox y un control de cuadro de edición, respectivamente.  
  
 Si el usuario cancela un cuadro de diálogo modal, la función miembro de `OnCancel` finaliza el cuadro de diálogo y `DoModal` devuelve el valor **IDCANCEL**.  En ese caso, no se cambia ningún dato entre el cuadro de diálogo y el objeto de cuadro de diálogo.  
  
## Vea también  
 [Intercambio y validación de datos de cuadros de diálogo](../mfc/dialog-data-exchange-and-validation.md)   
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)   
 [Validación de datos de cuadro de diálogo](../mfc/dialog-data-validation.md)