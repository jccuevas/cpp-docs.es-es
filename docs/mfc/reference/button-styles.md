---
title: "Estilos de bot&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BS_DEFPUSHBUTTON"
  - "BS_NOTIFY"
  - "BS_MULTILINE"
  - "BS_AUTOCHECKBOX"
  - "BS_3STATE"
  - "BS_BITMAP"
  - "BS_TOP"
  - "BS_PUSHBUTTON"
  - "BS_PUSHLIKE"
  - "BS_AUTO3STATE"
  - "BS_CHECKBOX"
  - "BS_AUTORADIOBUTTON"
  - "BS_RADIOBUTTON"
  - "BS_OWNERDRAW"
  - "BS_LEFT"
  - "BS_USERBUTTON"
  - "BS_RIGHTBUTTON"
  - "BS_RIGHT"
  - "BS_LEFTTEXT"
  - "BS_TEXT"
  - "BS_BOTTOM"
  - "BS_GROUPBOX"
  - "BS_FLAT"
  - "BS_VCENTER"
  - "BS_ICON"
  - "BS_CENTER"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BS_3STATE (constante)"
  - "BS_AUTO3STATE (constante)"
  - "BS_AUTOCHECKBOX (constante)"
  - "BS_AUTORADIOBUTTON (constante)"
  - "BS_BITMAP (constante)"
  - "BS_BOTTOM (constante)"
  - "BS_CENTER (constante)"
  - "BS_CHECKBOX (constante)"
  - "BS_DEFPUSHBUTTON (constante)"
  - "BS_FLAT (constante)"
  - "BS_GROUPBOX (constante)"
  - "BS_ICON (constante)"
  - "BS_LEFT (constante)"
  - "BS_LEFTTEXT (constante)"
  - "BS_MULTILINE (constante)"
  - "BS_NOTIFY (constante)"
  - "BS_OWNERDRAW (constante)"
  - "BS_PUSHBUTTON (constante)"
  - "BS_PUSHLIKE (constante)"
  - "BS_RADIOBUTTON (constante)"
  - "BS_RIGHT (constante)"
  - "BS_RIGHTBUTTON (constante)"
  - "BS_TEXT (constante)"
  - "BS_TOP (constante)"
  - "BS_USERBUTTON (constante)"
  - "BS_VCENTER (constante)"
  - "objetos de botón (CButton), estilos de botón"
  - "estilos, objetos de botón"
ms.assetid: 41206f72-2b92-4250-ae32-31184046402f
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# Estilos de bot&#243;n
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este tema se describen los tipos de botón y estilos.  
  
## Tipos de botón  
 En la tabla siguiente se enumeran tipos de botón.  Puede elegir opcionalmente uno de los siguientes.  Si no especifica un tipo de botón, el valor predeterminado es  `BS_PUSHBUTTON`.  
  
|Tipo|Descripción|  
|----------|-----------------|  
|`BS_3STATE`|Crea un botón de casilla con tres estados: `BST_CHECKED`, `BST_INDETERMINATE` y `BST_UNCHECKED`.  Al hacer clic en el botón, envía una notificación `BN_CLICKED` a la ventana propietaria, pero no cambia el estado del botón.  De forma predeterminada, el texto asociado se muestra a la derecha de la casilla.  Para mostrar texto a la izquierda de la casilla, utilice el estilo de `BS_LEFTTEXT` o de `BS_RIGHTBUTTON` .|  
|`BS_AUTO3STATE`|Crea un botón de casilla con tres estados: `BST_CHECKED`, `BST_INDETERMINATE` y `BST_UNCHECKED`.  Al hacer clic en el botón, envía una notificación `BN_CLICKED` a la ventana propietaria y cambia el estado del botón.  Los estados de botón completan un ciclo en el orden de `BST_CHECKED`, de `BST_INDETERMINATE` y de `BST_UNCHECKED`.  De forma predeterminada, el texto asociado se muestra a la derecha de la casilla.  Para mostrar texto a la izquierda de la casilla, utilice el estilo de `BS_LEFTTEXT` o de `BS_RIGHTBUTTON` .|  
|`BS_AUTOCHECKBOX`|Crea un botón de casilla con dos estados: `BST_CHECKED` y `BST_UNCHECKED`.  Al hacer clic en el botón, envía una notificación `BN_CLICKED` a la ventana propietaria y cambia el estado del botón.  De forma predeterminada, el texto asociado se muestra a la derecha de la casilla.  Para mostrar texto a la izquierda de la casilla, utilice el estilo de `BS_LEFTTEXT` o de `BS_RIGHTBUTTON` .|  
|`BS_AUTORADIOBUTTON`|Crea un botón de radio con dos estados: `BST_CHECKED` y `BST_UNCHECKED`.  Los botones de radio se utilizan normalmente en grupos, con cada grupo tiene un máximo de una opción activada al mismo tiempo.  Al hacer clic en el botón, envía una notificación `BN_CLICKED` a la ventana propietaria, establece el estado del botón de radio en el que se hizo clic en`BST_CHECKED`, así como los estados de todos los demás botones de radio del grupo de botones en `BST_UNCHECKED`.  De forma predeterminada, el texto asociado se muestra a la derecha del botón de radio.  Para mostrar texto a la izquierda del botón de radio, utilice el estilo `BS_LEFTTEXT` o `BS_RIGHTBUTTON` .|  
|`BS_CHECKBOX`|Crea un botón de casilla con dos estados: `BST_CHECKED` y `BST_UNCHECKED`.  Al hacer clic en el botón, envía una notificación `BN_CLICKED` a la ventana propietaria, pero no cambia el estado del botón.  De forma predeterminada, el texto asociado se muestra a la derecha de la casilla.  Para mostrar texto a la izquierda de la casilla, utilice el estilo de `BS_LEFTTEXT` o de `BS_RIGHTBUTTON` .|  
|`BS_COMMANDLINK`|Crea un botón de vínculo de comando.  Un botón de vínculo de comando es un botón de comando específico para [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] que muestra una flecha verde a la izquierda del texto principal y una nota debajo del texto principal.  Puede establecer el texto de la nota mediante [CButton::SetNote](../Topic/CButton::SetNote.md).|  
|`BS_DEFCOMMANDLINK`|Crea un botón de vínculo de comando.  Un botón de vínculo de comando es un botón de comando específico para [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] que muestra una flecha verde a la izquierda del texto principal y una nota debajo del texto principal.  Puede establecer el texto de la nota mediante [CButton::SetNote](../Topic/CButton::SetNote.md).  Si el botón está en un cuadro de diálogo, al presionar la tecla INTRO se envía una notificación de `BN_CLICKED` al cuadro de diálogo incluso cuando el botón no tiene el foco de entrada.|  
|`BS_DEFPUSHBUTTON`|Crea un botón de comando que tiene un borde negro intenso.  Si el botón está en un cuadro de diálogo, al presionar la tecla INTRO se envía una notificación de `BN_CLICKED` al cuadro de diálogo incluso cuando el botón no tiene el foco de entrada.|  
|`BS_DEFSPLITBUTTON`|Crea un botón de expansión.  Un botón de expansión es botón de comando específico en [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] que contiene un botón junto a la flecha de lista desplegable.  Al hacer clic en el botón, se ejecuta el comando predeterminado.  Al hacer clic en la flecha desplegable, aparece un menú de comandos adicionales.  Si el botón de expansión está en un cuadro de diálogo, al presionar la tecla INTRO se envía una notificación de `BN_CLICKED` al cuadro de diálogo incluso cuando el botón no tiene el foco de entrada.|  
|`BS_GROUPBOX`|Crea un rectángulo en el que otros botones pueden agruparse.  El texto asociado a este estilo se muestra en la esquina superior izquierda del rectángulo.|  
|`BS_OWNERDRAW`|Crea un botón dibujado por el propietario.  El marco de trabajo llama al método `DrawItem` cuando un aspecto visual del botón ha cambiado.  Este estilo debe establecerse cuando se utiliza la clase `CBitmapButton` .|  
|`BS_PUSHBUTTON`|Crea un botón de comando que envía una notificación `BN_CLICKED` a la ventana propietaria cuando el usuario hace clic en el botón.|  
|`BS_RADIOBUTTON`|Crea un botón de radio con dos estados: `BST_CHECKED` y `BST_UNCHECKED`.  Los botones de radio se utilizan normalmente en grupos, con cada grupo tiene un máximo de una opción activada al mismo tiempo.  Al hacer clic en el botón, envía una notificación `BN_CLICKED` a la ventana propietaria, pero el estado de los botones del grupo no cambia automáticamente.  De forma predeterminada, el texto asociado se muestra a la derecha del botón de radio.  Para mostrar texto a la izquierda del botón de radio, utilice el estilo `BS_LEFTTEXT` o `BS_RIGHTBUTTON` .|  
|`BS_SPLITBUTTON`|Crea un botón de expansión.  Un botón de expansión es botón de comando específico en [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] que contiene un botón junto a la flecha de lista desplegable.  Al hacer clic en el botón, se ejecuta el comando predeterminado.  Al hacer clic en la flecha desplegable, aparece un menú de comandos adicionales.|  
|`BS_USERBUTTON`|Obsoleta, pero se proporciona para la compatibilidad con las versiones de Windows de 16 bits.  Las aplicaciones basadas en win32 deben utilizar `BS_OWNERDRAW` en su lugar.|  
  
## Estilos de botón de radio y casilla  
 En la tabla siguiente se enumeran los estilos que son específicos de los botones de radio y de las casillas.  Estos estilos se omiten en todos los demás tipos de botón.  Puede elegir opcionalmente uno o más de los siguientes.  
  
|Estilo|Descripción|  
|------------|-----------------|  
|`BS_LEFTTEXT`|Cuando se combina con un estilo de botón de radio o casilla, el texto aparece en el lado izquierdo del botón de radio o de la casilla.|  
|`BS_RIGHTBUTTON`|Cuando se combina con un estilo de botón de radio o casilla, el texto aparece en el lado izquierdo del botón de radio o de la casilla.  Este estilo es idéntico al estilo `BS_LEFTTEXT`.|  
|`BS_PUSHLIKE`|Hace que una casilla o un botón de radio tengan la apariencia y el comportamiento de un botón de comando.  El botón aparece presionado cuando su estado es `BST_CHECKED`, presionado y atenuado cuando su estado es `BST_INDETERMINATE` y liberado cuando su estado es `BST_UNCHECKED`.|  
  
## Estilos de alineación de texto  
 En la tabla siguiente se enumeran las opciones de alineación de texto horizontal y vertical.  Puede elegir opcionalmente uno de los siguientes.  
  
|Estilo|Descripción|  
|------------|-----------------|  
|`BS_LEFT`|Alinea a la izquierda el texto del rectángulo del botón.  Sin embargo, si el botón es una casilla o un botón de radio que no tienen el estilo de `BS_RIGHTBUTTON`, el texto se alinea a la izquierda en la parte derecha de la casilla o botón de radio.|  
|`BS_RIGHT`|Alinea a la derecha el texto del rectángulo del botón.  Sin embargo, si el botón es una casilla o un botón de radio que no tienen el estilo de `BS_RIGHTBUTTON`, el texto se alinea a la derecha en la parte derecha de la casilla o botón de radio.|  
|`BS_CENTER`|Los centros texto horizontalmente en el rectángulo del botón.|  
|`BS_TOP`|Coloca texto en la parte superior del rectángulo del botón.|  
|`BS_BOTTOM`|Coloca texto en la parte inferior del rectángulo del botón.|  
|`BS_VCENTER`|Los centros texto verticalmente en el rectángulo del botón.|  
  
## Opciones de contenido del botón  
 En la tabla siguiente se enumeran las opciones que indican lo que se muestra en el botón.  Los tipos de botón que solo muestran el texto omiten estos estilos.  Puede elegir opcionalmente uno de los siguientes.  
  
|Estilo|Descripción|  
|------------|-----------------|  
|`BS_BITMAP`|Especifica que el botón muestra un mapa de bits.|  
|`BS_ICON`|Especifica que el botón muestra un icono.|  
|`BS_TEXT`|Especifica que el botón muestra texto.|  
  
## Otras opciones  
 En la tabla siguiente se enumeran las opciones adicionales que se pueden utilizar con cualquier tipo de botón.  Puede elegir opcionalmente uno o más de los siguientes.  
  
|Estilo|Descripción|  
|------------|-----------------|  
|`BS_FLAT`|Especifica que el botón es bidimensional y no se dibuja con el sombreado predeterminado para crear una imagen tridimensional.|  
|`BS_MULTILINE`|Incluye el texto del botón en varias líneas si la cadena de texto es demasiado larga para que quepa en una única línea en el rectángulo del botón.|  
|`BS_NOTIFY`|Habilita un botón para enviar `BN_DBLCLK`, `BN_KILLFOCUS` y mensajes de notificación `BN_SETFOCUS` a su ventana primaria.  Observe que los botones envían la notificación de `BN_CLICKED` independientemente de si el estilo está especificado.|  
  
## Vea también  
 [Estilos utilizados por MFC](../../mfc/reference/styles-used-by-mfc.md)   
 [CButton::Create](../Topic/CButton::Create.md)   
 [Estilos de botón](http://msdn.microsoft.com/library/windows/desktop/bb775951)   
 [BN\_CLICKED Notification](_win32_bn_clicked_notification)