---
title: "Implementing a Window with CWindowImpl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CWindowImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, ventanas"
  - "subclassing ATL window classes"
  - "superclassing, ATL"
  - "windows [C++], ATL"
  - "windows [C++], subclassing"
  - "windows [C++], superclassing"
ms.assetid: 3fc40550-f1d6-4702-8b7c-4cf682b6a855
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Implementing a Window with CWindowImpl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para implementar una ventana, derive una clase de `CWindowImpl`.  En la clase derivada, declare un mapa de mensajes y el controlador de mensajes funciona.  Ahora puede utilizar la clase de tres maneras diferentes:  
  
-   [Cree una ventana basada en una clase de Windows](#_atl_creating_a_window_based_on_a_new_windows_class)  
  
-   [Superclase una clase existente de Windows](#_atl_superclassing_an_existing_windows_class)  
  
-   [Cree subclases una ventana existente](#_atl_subclassing_an_existing_window)  
  
##  <a name="_atl_creating_a_window_based_on_a_new_windows_class"></a> Crear una ventana basada en una nueva clase Windows  
 `CWindowImpl` contiene la macro de [DECLARE\_WND\_CLASS](../Topic/DECLARE_WND_CLASS.md) para declarar la información de clase de Windows.  Esta macro implementa la función de `GetWndClassInfo` , que utiliza [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) para definir información de una clase de Windows.  Cuando se llama a `CWindowImpl::Create` , se registra esta clase de Windows y se crea una nueva ventana.  
  
> [!NOTE]
>  `CWindowImpl` pasa **NULL** a la macro de `DECLARE_WND_CLASS` , que significa que ATL generará un nombre de clase de Windows.  Para especificar su propio nombre, pase una cadena a `DECLARE_WND_CLASS` en su `CWindowImpl`\- clase derivada.  
  
## Ejemplo  
 A continuación se muestra un ejemplo de una clase que implementa una ventana basada en una clase de Windows:  
  
 [!code-cpp[NVC_ATL_Windowing#64](../atl/codesnippet/CPP/implementing-a-window-with-cwindowimpl_1.h)]  
  
 Para crear una ventana, cree una instancia de `CMyWindow` y llame al método de **Create** .  
  
> [!NOTE]
>  Para invalidar la información predeterminada de la clase de Windows, implemente el método de `GetWndClassInfo` en la clase derivada estableciendo los miembros de `CWndClassInfo` con los valores apropiados.  
  
##  <a name="_atl_superclassing_an_existing_windows_class"></a> Crear utiliza una clase existente Windows  
 La macro de [DECLARE\_WND\_SUPERCLASS](../Topic/DECLARE_WND_SUPERCLASS.md) permite crear una ventana que utiliza una clase existente de Windows.  Especifique esta macro en la `CWindowImpl`\- clase derivada.  Como cualquier otra ventana ATL, los mensajes son controlados por un mapa de mensajes.  
  
 Cuando se utiliza `DECLARE_WND_SUPERCLASS`, una clase de Windows se registrada.  Esta nueva clase será igual que la clase existente especifica, pero reemplazar el procedimiento de ventana con `CWindowImpl::WindowProc` \(o con la función que invalida este método\).  
  
## Ejemplo  
 A continuación se muestra un ejemplo de una clase que utiliza la clase estándar de edición:  
  
 [!code-cpp[NVC_ATL_Windowing#65](../atl/codesnippet/CPP/implementing-a-window-with-cwindowimpl_2.h)]  
  
 Para crear la ventana creada superclase de edición, cree una instancia de `CMyEdit` y llame al método de **Create** .  
  
##  <a name="_atl_subclassing_an_existing_window"></a> Crear subclases de una ventana existente  
 Para crear subclases de una ventana existente, derive una clase de `CWindowImpl` y declarar un mapa de mensajes, como en los dos casos anteriores.  Observe, sin embargo, que no especifica ninguna información de clase de Windows, ya que creará subclases una ventana ya existente.  
  
 En lugar de llamar a **Create**, llame a `SubclassWindow` y pase el identificador de la ventana existente que desea crear subclases.  Una vez que la ventana tiene subclases, utilizará `CWindowImpl::WindowProc` \(o la función que invalida este método\) para enviar mensajes al mapa de mensajes.  Para desasociar una ventana derivado del objeto, llame a `UnsubclassWindow`.  El procedimiento de ventana original de la ventana se restaurado.  
  
## Vea también  
 [Implementing a Window](../atl/implementing-a-window.md)