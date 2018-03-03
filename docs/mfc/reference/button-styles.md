---
title: Estilos de los botones | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BS_DEFPUSHBUTTON
- BS_NOTIFY
- BS_MULTILINE
- BS_AUTOCHECKBOX
- BS_3STATE
- BS_BITMAP
- BS_TOP
- BS_PUSHBUTTON
- BS_PUSHLIKE
- BS_AUTO3STATE
- BS_CHECKBOX
- BS_AUTORADIOBUTTON
- BS_RADIOBUTTON
- BS_OWNERDRAW
- BS_LEFT
- BS_USERBUTTON
- BS_RIGHTBUTTON
- BS_RIGHT
- BS_LEFTTEXT
- BS_TEXT
- BS_BOTTOM
- BS_GROUPBOX
- BS_FLAT
- BS_VCENTER
- BS_ICON
- BS_CENTER
dev_langs:
- C++
helpviewer_keywords:
- BS_NOTIFY constant [MFC]
- BS_RIGHTBUTTON constant [MFC]
- styles [MFC], button objects
- BS_USERBUTTON constant [MFC]
- BS_VCENTER constant [MFC]
- BS_PUSHLIKE constant [MFC]
- BS_RADIOBUTTON constant [MFC]
- BS_PUSHBUTTON constant [MFC]
- BS_DEFPUSHBUTTON constant [MFC]
- BS_LEFTTEXT constant [MFC]
- button objects (CButton), button styles
- BS_AUTO3STATE constant [MFC]
- BS_3STATE constant [MFC]
- BS_OWNERDRAW constant [MFC]
- BS_AUTORADIOBUTTON constant [MFC]
- BS_GROUPBOX constant [MFC]
- BS_BITMAP constant [MFC]
- BS_CENTER constant [MFC]
- BS_MULTILINE constant [MFC]
- BS_BOTTOM constant [MFC]
- BS_FLAT constant [MFC]
- BS_AUTOCHECKBOX constant [MFC]
- BS_RIGHT constant [MFC]
- BS_CHECKBOX constant [MFC]
- BS_LEFT constant [MFC]
- BS_ICON constant [MFC]
- BS_TOP constant [MFC]
- BS_TEXT constant
ms.assetid: 41206f72-2b92-4250-ae32-31184046402f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b9ed2dcffbcd45215008b3d0caa802a5384367b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="button-styles"></a>Estilos de botón
Este tema describe los estilos y tipos de botones.  
  
## <a name="button-types"></a>Tipos de botones  
 En la tabla siguiente se enumera los tipos de botón. Si lo desea, puede elegir uno de los siguientes. Si no especifica un tipo de botón, el valor predeterminado es `BS_PUSHBUTTON`.  
  
|Tipo|Descripción|  
|----------|-----------------|  
|`BS_3STATE`|Crea un botón de casilla de verificación con tres estados: `BST_CHECKED`, `BST_INDETERMINATE`, y `BST_UNCHECKED`. Al hacer clic en el botón envía una `BN_CLICKED` notificación a la ventana propietaria pero no cambia el estado del botón. De forma predeterminada, se muestra el texto asociado a la derecha de la casilla de verificación. Para mostrar texto a la izquierda de la casilla de verificación, utilice la `BS_LEFTTEXT` o `BS_RIGHTBUTTON` estilo.|  
|`BS_AUTO3STATE`|Crea un botón de casilla de verificación con tres estados: `BST_CHECKED`, `BST_INDETERMINATE`, y `BST_UNCHECKED`. Al hacer clic en el botón envía una `BN_CLICKED` notificación a la ventana propietaria y cambia el estado del botón. El botón indica ciclo en el orden de `BST_CHECKED`, `BST_INDETERMINATE`, y `BST_UNCHECKED`. De forma predeterminada, se muestra el texto asociado a la derecha de la casilla de verificación. Para mostrar texto a la izquierda de la casilla de verificación, utilice la `BS_LEFTTEXT` o `BS_RIGHTBUTTON` estilo.|  
|`BS_AUTOCHECKBOX`|Crea un botón de casilla de verificación con dos estados: `BST_CHECKED` y `BST_UNCHECKED`. Al hacer clic en el botón envía una `BN_CLICKED` notificación a la ventana propietaria y cambia el estado del botón. De forma predeterminada, se muestra el texto asociado a la derecha de la casilla de verificación. Para mostrar texto a la izquierda de la casilla de verificación, utilice la `BS_LEFTTEXT` o `BS_RIGHTBUTTON` estilo.|  
|`BS_AUTORADIOBUTTON`|Crea un botón de radio con dos estados: `BST_CHECKED` y `BST_UNCHECKED`. Botones de radio generalmente se utilizan en grupos, con cada grupo con un máximo de una opción con marca a la vez. Al hacer clic en el botón envía una `BN_CLICKED` notificación a la ventana propietaria, Establece el estado del botón de radio donde ha hecho clic en `BST_CHECKED`y establece los Estados de todos los demás botones de radio en el grupo de botones para `BST_UNCHECKED`. De forma predeterminada, se muestra el texto asociado a la derecha del botón de radio. Para mostrar texto a la izquierda del botón de radio, utilice la `BS_LEFTTEXT` o `BS_RIGHTBUTTON` estilo.|  
|`BS_CHECKBOX`|Crea un botón de casilla de verificación con dos estados: `BST_CHECKED` y `BST_UNCHECKED`. Al hacer clic en el botón envía una `BN_CLICKED` notificación a la ventana propietaria pero no cambia el estado del botón. De forma predeterminada, se muestra el texto asociado a la derecha de la casilla de verificación. Para mostrar texto a la izquierda de la casilla de verificación, utilice la `BS_LEFTTEXT` o `BS_RIGHTBUTTON` estilo.|  
|`BS_COMMANDLINK`|Crea un botón de vínculo de comando. Un botón de vínculo de comando es un botón de comando específico [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] que muestra una flecha verde a la izquierda del texto principal y una nota debajo del texto principal. Puede establecer el texto de nota con [CButton::SetNote](../../mfc/reference/cbutton-class.md#setnote).|  
|`BS_DEFCOMMANDLINK`|Crea un botón de vínculo de comando. Un botón de vínculo de comando es un botón de comando específico [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] que muestra una flecha verde a la izquierda del texto principal y una nota debajo del texto principal. Puede establecer el texto de nota con [CButton::SetNote](../../mfc/reference/cbutton-class.md#setnote). Si el botón está en un cuadro de diálogo, presione el ENTRAR clave envía una `BN_CLICKED` notificación al cuadro de diálogo, incluso cuando el botón no tiene el foco de entrada.|  
|`BS_DEFPUSHBUTTON`|Crea un botón de comando que tiene un borde negro grueso. Si el botón está en un cuadro de diálogo, presione el ENTRAR clave envía una `BN_CLICKED` notificación al cuadro de diálogo, incluso cuando el botón no tiene el foco de entrada.|  
|`BS_DEFSPLITBUTTON`|Crea un botón de expansión. Un botón de expansión es un botón de comando específico de [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] que contiene un botón adyacente a una flecha de lista desplegable. Al hacer clic en el botón, se ejecuta el comando predeterminado. Al hacer clic en la flecha de lista desplegable, aparece un menú de comandos adicionales. Si el botón de expansión está en un cuadro de diálogo, presione el ENTRAR clave envía una `BN_CLICKED` notificación al cuadro de diálogo, incluso cuando el botón no tiene el foco de entrada|  
|`BS_GROUPBOX`|Crea un rectángulo en el que se pueden agrupar otros botones. Texto asociado con este estilo se muestra en la esquina superior izquierda de un rectángulo.|  
|`BS_OWNERDRAW`|Crea un botón dibujado por el propietario. Las llamadas de framework la `DrawItem` método cuando un aspecto visual del botón ha cambiado. Este estilo debe establecerse cuando se usa el `CBitmapButton` clase.|  
|`BS_PUSHBUTTON`|Crea un botón de comando que envía un `BN_CLICKED` notificación a la ventana propietaria cuando el usuario hace clic en el botón.|  
|`BS_RADIOBUTTON`|Crea un botón de radio con dos estados: `BST_CHECKED` y `BST_UNCHECKED`. Botones de radio generalmente se utilizan en grupos, con cada grupo con un máximo de una opción con marca a la vez. Al hacer clic en el botón envía una `BN_CLICKED` notificación a la ventana propietaria pero no cambia automáticamente el estado de cualquier botón del grupo. De forma predeterminada, se muestra el texto asociado a la derecha del botón de radio. Para mostrar texto a la izquierda del botón de radio, utilice la `BS_LEFTTEXT` o `BS_RIGHTBUTTON` estilo.|  
|`BS_SPLITBUTTON`|Crea un botón de expansión. Un botón de expansión es un botón de comando específico de [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] que contiene un botón adyacente a una flecha de lista desplegable. Al hacer clic en el botón, se ejecuta el comando predeterminado. Al hacer clic en la flecha de lista desplegable, aparece un menú de comandos adicionales.|  
|`BS_USERBUTTON`|Obsoleta, pero se proporciona para la compatibilidad con versiones de 16 bits de Windows. Las aplicaciones basadas en Win32 deben utilizar `BS_OWNERDRAW` en su lugar.|  
  
## <a name="radio-button-and-check-box-styles"></a>Botón de radio y casilla de verificación estilos  
 En la tabla siguiente se enumera los estilos que son específicos de los botones de radio y casillas de verificación. Estos estilos se omiten en todos los demás tipos de botón. Si lo desea, puede elegir una o varias de las siguientes acciones.  
  
|Estilo|Descripción|  
|-----------|-----------------|  
|`BS_LEFTTEXT`|Cuando se combina con un estilo de casilla de verificación o botón de radio, el texto aparece en el lado izquierdo de la casilla de verificación o un botón de radio.|  
|`BS_RIGHTBUTTON`|Cuando se combina con un estilo de casilla de verificación o botón de radio, el texto aparece en el lado izquierdo de la casilla de verificación o un botón de radio. Este estilo es idéntica a la `BS_LEFTTEXT` estilo.|  
|`BS_PUSHLIKE`|Hace que una casilla de verificación o un botón de radio aspecto y comportamiento que un botón de comando. El botón correspondiente aparece seleccionado cuando su estado es `BST_CHECKED`, presiona y atenuado cuando su estado es `BST_INDETERMINATE`y se liberan cuando su estado es `BST_UNCHECKED`.|  
  
## <a name="text-alignment-styles"></a>Estilos de alineación de texto  
 La tabla siguiente enumera las opciones de alineación de texto horizontal y vertical. Si lo desea, puede elegir uno de los siguientes.  
  
|Estilo|Descripción|  
|-----------|-----------------|  
|`BS_LEFT`|Alinea el texto en el rectángulo de botón a la izquierda. Sin embargo, si el botón aparece una casilla o botón de opción que no tiene la `BS_RIGHTBUTTON` estilo, se deja el texto alineado a la derecha de la casilla de verificación o un botón de radio.|  
|`BS_RIGHT`|Alinea el texto en el rectángulo de botón a la derecha. Sin embargo, si el botón aparece una casilla o botón de opción que no tiene la `BS_RIGHTBUTTON` de estilo, el texto está derecho alineado a la derecha de la casilla de verificación o un botón de radio.|  
|`BS_CENTER`|Centra el texto horizontalmente en el rectángulo de botón.|  
|`BS_TOP`|Coloca el texto en la parte superior del rectángulo de botón.|  
|`BS_BOTTOM`|Coloca el texto en la parte inferior del rectángulo de botón.|  
|`BS_VCENTER`|Centra el texto verticalmente en el rectángulo de botón.|  
  
## <a name="button-content-options"></a>Opciones de contenido de botón  
 En la tabla siguiente se enumera las opciones que indican lo que se muestra en el botón. Tipos de botones que se muestran solo texto omitir estos estilos. Si lo desea, puede elegir uno de los siguientes.  
  
|Estilo|Descripción|  
|-----------|-----------------|  
|`BS_BITMAP`|Especifica que el botón muestra un mapa de bits.|  
|`BS_ICON`|Especifica que el botón muestre un icono.|  
|`BS_TEXT`|Especifica que el botón muestra el texto.|  
  
## <a name="other-options"></a>Otras opciones  
 En la tabla siguiente se enumera otras opciones adicionales que puede usar con cualquier tipo de botón. Si lo desea, puede elegir una o varias de las siguientes acciones.  
  
|Estilo|Descripción|  
|-----------|-----------------|  
|`BS_FLAT`|Especifica que el botón es bidimensional y no se dibuja con sombreado de forma predeterminada para crear una imagen tridimensional.|  
|`BS_MULTILINE`|Ajusta el texto del botón a varias líneas si la cadena de texto es demasiado larga para caber en una sola línea en el rectángulo de botón.|  
|`BS_NOTIFY`|Habilita un botón Enviar `BN_DBLCLK`, `BN_KILLFOCUS`, y `BN_SETFOCUS` mensajes de notificación a su ventana primaria. Tenga en cuenta que los botones de envío el `BN_CLICKED` notificación independientemente de si se ha especificado este estilo.|  
  
## <a name="see-also"></a>Vea también  
 [Estilos utilizados por MFC](../../mfc/reference/styles-used-by-mfc.md)   
 [CButton::Create](../../mfc/reference/cbutton-class.md#create) [estilos de botón](http://msdn.microsoft.com/library/windows/desktop/bb775951)   



