---
title: "TN017: Destruir objetos Window | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.objects"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "destruir ventanas"
  - "PostNcDestroy (método)"
  - "TN017"
ms.assetid: 5bf208a5-5683-439b-92a1-547c5ded26cd
caps.latest.revision: 15
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN017: Destruir objetos Window
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Esta nota describe el uso del método de [CWnd::PostNcDestroy](../Topic/CWnd::PostNcDestroy.md) .  Utilice este método si desea realizar la asignación personalizada de `CWnd`\- objetos derivados.  Esta cuenta también explica por qué debe utilizar [CWnd::DestroyWindow](../Topic/CWnd::DestroyWindow.md) para destruir el objeto en cuestión. Windows en lugar del operador de `delete` .  
  
 Si sigue las instrucciones de este tema, tendrá pocos problemas de limpieza.  Estos problemas pueden ser el resultado de problemas como olvidar eliminar y memoria de C\+\+, olvidar liberar recursos del sistema como s para `HWND`, o liberar objetos demasiadas veces.  
  
## El problema  
 Cada objeto de ventanas \(objeto de una clase derivada de `CWnd`\) representa el objeto en cuestión. y `HWND`.  Los objetos de C\+\+ se asignan en la pila de aplicación y s para `HWND`es asignada en recursos del sistema por el administrador de ventanas.  Porque hay varias maneras de destruir un objeto en la ventana, se debe proporcionar un conjunto de reglas que impiden que el recurso del sistema o pérdidas de memoria.  Estas reglas también deben evitar que los objetos y los identificadores de Windows son destruidos más de una vez.  
  
## Windows de destrucción  
 Los siguientes son las dos maneras permitidas de destruir un objeto de Windows:  
  
-   Llamada `CWnd::DestroyWindow` o la API de Windows `DestroyWindow`.  
  
-   Explícitamente eliminando con el operador de `delete` .  
  
 El primer caso es con mucho la más comunes.  Este caso se aplica incluso si el código no llama a `DestroyWindow` directamente.  Cuando el usuario cierra directamente una ventana de marco, esta acción genera el mensaje de `WM_CLOSE` , y respuesta predeterminada a este mensaje es llamar `DestroyWindow.` Cuando se destruye una ventana primaria, llamadas `DestroyWindow` de Windows para todos sus elementos secundarios.  
  
 El segundo caso, el uso del operador de `delete` en los objetos de Windows, debe ser poco frecuente.  Se algunos casos los siguientes donde mediante `delete` son la opción correcta.  
  
## Limpieza auto con CWnd::PostNcDestroy  
 Cuando el sistema destruye una ventana de Windows, el mensaje de Windows del último enviado a la ventana es `WM_NCDESTROY`.  El controlador predeterminado de `CWnd` para ese mensaje es [CWnd::OnNcDestroy](../Topic/CWnd::OnNcDestroy.md).  `OnNcDestroy` desasociará `HWND` de objeto de C\+\+ y llamará a la función virtual `PostNcDestroy`.  Algunas clases reemplazan esta función para eliminar el objeto de C\+\+.  
  
 La implementación predeterminada de `CWnd::PostNcDestroy` no hace nada, adecuado para los objetos de la ventana que se asignan en el marco de pila o se insertan en otros objetos.  Esto no es adecuado para los objetos de la ventana que están diseñados para ser asignados en el montón sin otros objetos.  Es decir no es adecuado para los objetos de la ventana que no se incrustan en otros objetos de C\+\+.  
  
 Las clases que están diseñados para ser asignadas sólo en la invalidación de la pila el método de `PostNcDestroy` para realizar `delete this`.  Esta instrucción libere la memoria asociada al objeto de C\+\+.  Aunque el valor predeterminado `CWnd` destructor llama `DestroyWindow` si `m_hWnd` no es null, no se realiza una recursividad infinita que el identificador se desasoció y NULL durante la fase de limpieza.  
  
> [!NOTE]
>  El sistema llama normalmente `CWnd::PostNcDestroy` después de procesar el mensaje de Windows `WM_NCDESTROY` y `HWND` y el objeto de la ventana de C\+\+ están conectados ya no.  El sistema también llamará `CWnd::PostNcDestroy` en la implementación de la mayoría de las llamadas de [CWnd::Create](../Topic/CWnd::Create.md) si el error.  Las reglas automático de limpieza se describen más adelante en este tema.  
  
## Clases automático de limpieza  
 Las clases siguientes no están diseñados para la auto\- limpieza.  Se insertan normalmente en otros objetos de C\+\+ o en el montón:  
  
-   Todos los controles estándar de Windows \(`CStatic`, `CEdit`, `CListBox`, etc.\).  
  
-   Cualquier ventanas secundarias derivadas directamente de `CWnd` \(por ejemplo, controles personalizados\).  
  
-   Ventanas divisoras \(`CSplitterWnd`\).  
  
-   Barras de control predeterminadas \(las clases derivadas de `CControlBar`, vea [Nota técnica 31](../mfc/tn031-control-bars.md) para habilitar el auto\- DELETE para los objetos de la barra de control\).  
  
-   Cuadros de diálogo \(`CDialog`\) diseñados para los cuadros de diálogo modales en el marco de pila.  
  
-   Todos los cuadros de diálogo del estándar excepto `CFindReplaceDialog`.  
  
-   Los diálogos predeterminados creados por ClassWizard.  
  
 Las clases siguientes están diseñados para la auto\- limpieza.  Se asignan normalmente solo en el montón:  
  
-   Ventanas de marco principal \(derivadas directa o indirectamente de `CFrameWnd`\).  
  
-   Ventanas de vista \(derivadas directa o indirectamente de `CView`\).  
  
 Si desea interrumpir estas reglas, debe reemplazar el método de `PostNcDestroy` en la clase derivada.  Para agregar auto\- limpieza a la clase, llame a la clase base y haga `delete this`.  Para quitar auto\- limpieza de la clase, llame a `CWnd::PostNcDestroy` directamente en lugar del método de `PostNcDestroy` de la clase base directa.  
  
 El uso más común de cambiar el comportamiento automático de limpieza es crear un diálogo no modal que se puede asignar en la pila.  
  
## Cuándo llamar a delete  
 Se recomienda llamar `DestroyWindow` destruir un objeto de Windows, el método de C\+\+ o `DestroyWindow` global API.  
  
 No llame a `DestroyWindow` global API para destruir una ventana secundaria de MDI.  Debe utilizar el método virtual `CWnd::DestroyWindow` en su lugar.  
  
 Para los objetos de la ventana de C\+\+ que no realizan auto\- limpieza, mediante el operador de `delete` puede producir una pérdida de memoria cuando se intenta llamar a `DestroyWindow` en `CWnd::~CWnd` destructor si el VTBL no indica correctamente a la clase derivada.  Esto ocurre porque el sistema no encuentra el adecuado destruye método para llamar a.  Mediante `DestroyWindow` en lugar de `delete` evita estos problemas.  Esto puede ser un error sutil, la compilación en modo de depuración generará la advertencia siguiente si pueden producirse problemas.  
  
```  
Warning: calling DestroyWindow in CWnd::~CWnd  
   OnDestroy or PostNcDestroy in derived class will not be called  
```  
  
 En el caso de objetos de C\+\+ Windows que realizan auto\- limpieza, debe llamar a `DestroyWindow`.  Si se utiliza el operador de `delete` directamente, el asignador de memoria para diagnósticos de MFC lo notificará que está liberando memoria dos veces.  Las dos instancias son la primera llamada explícita y la llamada indirecta a `delete this` en la implementación de la auto\- limpieza de `PostNcDestroy`.  
  
 Después de llamar a `DestroyWindow` en un objeto de la no\-auto\- limpieza, el objeto C\+\+ todavía estará sobre, pero `m_hWnd` serán NULL.  Después de llamar a `DestroyWindow` en un objeto de la auto\- limpieza, el objeto C\+\+ se salido, liberar con el operador delete de C\+\+ en la implementación de la auto\- limpieza de `PostNcDestroy`.  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)