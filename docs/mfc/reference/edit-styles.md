---
title: "Estilos de edición | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ES_READONLY
- ES_WANTRETURN
- ES_UPPERCASE
- ES_NUMBER
- ES_AUTOHSCROLL
- ES_LOWERCASE
- ES_RIGHT
- ES_MULTILINE
- ES_PASSWORD
- ES_NOHIDESEL
- ES_OEMCONVERT
- ES_LEFT
- ES_CENTER
dev_langs:
- C++
helpviewer_keywords:
- ES_WANTRETURN constant
- edit styles [MFC]
- ES_RIGHT constant
- ES_READONLY constant
- ES_PASSWORD constant
- ES_MULTILINE constant
- ES_LEFT constant
- ES_AUTOVSCROLL constant
- ES_OEMCONVERT constant
- ES_LOWERCASE constant
- ES_NUMBER constant
- ES_UPPERCASE constant
- ES_NOHIDESEL constant
- ES_AUTOHSCROLL constant
- ES_CENTER constant
ms.assetid: e6291dd6-f2cb-4ce2-ac31-32272526625c
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 275e0d2dede038bdbe9061bc8051408442aa70bf
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="edit-styles"></a>Estilos de edición
-   **ES_AUTOHSCROLL** desplaza automáticamente el texto a la derecha 10 caracteres cuando el usuario escribe un carácter al final de la línea. Cuando el usuario presiona la tecla ENTRAR, el control desplaza todo el texto a la posición 0.  
  
-   **ES_AUTOVSCROLL** se desplaza automáticamente a texto de una página cuando el usuario presiona ENTRAR en la última línea.  
  
-   **ES_CENTER** centra el texto en una sola línea o varias líneas de control de edición.  
  
-   **ES_LEFT** control de edición de texto alinea a la izquierda en una sola línea o varias líneas.  
  
-   **ES_LOWERCASE** convierte todos los caracteres a minúsculas, según se escriben en el control de edición.  
  
-   **ES_MULTILINE** designa un control de edición de varias líneas. (El valor predeterminado es una línea única). Si el **ES_AUTOVSCROLL** se especifica el estilo, el control de edición muestra tantas líneas como sea posible y desplaza verticalmente cuando el usuario presiona la tecla ENTRAR. Si **ES_AUTOVSCROLL** no es proporciona el control de edición muestra tantas líneas como sea posible y sonidos si se presiona ENTRAR cuando no hay más líneas que se pueden mostrar. Si el **ES_AUTOHSCROLL** se especifica el estilo, el control de edición de varias líneas desplaza automáticamente horizontalmente cuando el símbolo de intercalación va más allá del borde derecho del control. Para iniciar una nueva línea, el usuario debe presionar ENTRAR. Si **ES_AUTOHSCROLL** no es proporciona el control ajusta automáticamente las palabras al principio de la línea siguiente cuando es necesario; también se iniciará una nueva línea si se presiona ENTRAR. La posición de la wordwrap está determinada por el tamaño de ventana. Si se cambia el tamaño de la ventana, cambia la posición de ajuste de línea y el texto se vuelve a mostrar. Controles de edición de varias líneas pueden tener barras de desplazamiento. Un control de edición con barras de desplazamiento procesa sus propios mensajes de la barra de desplazamiento. Editar controles sin desplazamiento de las barras de desplazamiento como se describió anteriormente y procesar los mensajes de desplazamiento enviados por la ventana primaria.  
  
-   **ES_NOHIDESEL** normalmente, oculta la selección en un control de edición cuando el control pierde el foco de entrada e invierte la selección cuando el control recibe el foco de entrada. Especificar **ES_NOHIDESEL** elimina esta acción predeterminada.  
  
-   **ES_NUMBER** permite sólo los dígitos que se escriban en el control de edición.  
  
-   **ES_OEMCONVERT** texto escrito en el control de edición se convierte del juego de caracteres ANSI en el conjunto de caracteres OEM y de nuevo a ANSI. Esto garantiza la conversión correcta de caracteres cuando la aplicación llama el `AnsiToOem` función de Windows para convertir una cadena ANSI en el control de edición en caracteres OEM. Este estilo es más útil para controles de edición que contienen nombres de archivo.  
  
-   **ES_PASSWORD** muestra todos los caracteres como un asterisco (**\***) mientras se escribe en el control de edición. Una aplicación puede utilizar el `SetPasswordChar` función miembro para cambiar el carácter que se muestra.  
  
-   **ES_READONLY** impide que el usuario escribe o edita el texto del control de edición.  
  
-   **ES_RIGHT** control de edición de texto alinea a la derecha en una sola línea o varias líneas.  
  
-   **ES_UPPERCASE** convierte todos los caracteres a mayúsculas cuando se escriben en el control de edición.  
  
-   **ES_WANTRETURN** especifica que se inserte un retorno de carro cuando el usuario presiona la tecla ENTRAR mientras escribe texto en un control de edición de varias líneas en un cuadro de diálogo. Sin este estilo, presionar la tecla ENTRAR tiene el mismo efecto que si se presiona el pushbutton predeterminado de cuadros de diálogo. Este estilo no tiene ningún efecto en una sola línea control de edición.  
  
## <a name="see-also"></a>Vea también  
 [Estilos utilizados por MFC](../../mfc/reference/styles-used-by-mfc.md)   
 [CEdit::Create](../../mfc/reference/cedit-class.md#create)   
 [Edición de estilos de Control](http://msdn.microsoft.com/library/windows/desktop/bb775464)


