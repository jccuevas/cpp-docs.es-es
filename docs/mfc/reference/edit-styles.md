---
title: "Estilos de edici&#243;n | Microsoft Docs"
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
  - "ES_READONLY"
  - "ES_WANTRETURN"
  - "ES_UPPERCASE"
  - "ES_NUMBER"
  - "ES_AUTOHSCROLL"
  - "ES_LOWERCASE"
  - "ES_RIGHT"
  - "ES_MULTILINE"
  - "ES_PASSWORD"
  - "ES_NOHIDESEL"
  - "ES_OEMCONVERT"
  - "ES_LEFT"
  - "ES_CENTER"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "estilos de edición [MFC]"
  - "ES_AUTOHSCROLL (constante)"
  - "ES_AUTOVSCROLL (constante)"
  - "ES_CENTER (constante)"
  - "ES_LEFT (constante)"
  - "ES_LOWERCASE (constante)"
  - "ES_MULTILINE (constante)"
  - "ES_NOHIDESEL (constante)"
  - "ES_NUMBER (constante)"
  - "ES_OEMCONVERT (constante)"
  - "ES_PASSWORD (constante)"
  - "ES_READONLY (constante)"
  - "ES_RIGHT (constante)"
  - "ES_UPPERCASE (constante)"
  - "ES_WANTRETURN (constante)"
ms.assetid: e6291dd6-f2cb-4ce2-ac31-32272526625c
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Estilos de edici&#243;n
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

-   Los desplazamientos de**ES\_AUTOHSCROLL**automáticamente el texto a la derecha en 10 caracteres cuando el usuario escribe un carácter al final de la línea.  Cuando el usuario presiona la tecla ENTRAR, el control se mueve todo el texto de nuevo a la posición 0.  
  
-   Los desplazamientos de**ES\_AUTOVSCROLL**automáticamente el texto hacia arriba una página cuando el usuario presione ENTRAR en la última línea.  
  
-   Los centros de**ES\_CENTER**escribe texto en un control de una línea o de edición de varias líneas.  
  
-   **ES\_LEFT** Izquierdo\- alinea el texto en un control de una línea o de edición de varias líneas.  
  
-   **ES\_LOWERCASE** convierte todos los caracteres en minúsculas a medida que se escriben en el control de edición.  
  
-   **ES\_MULTILINE** Designates un control de edición de varias líneas. \(El valor predeterminado es única línea\). Si se especifica el estilo de **ES\_AUTOVSCROLL** , el control de edición muestra tantas líneas posible y verticalmente cuando el usuario presiona la tecla ENTRAR.  Si **ES\_AUTOVSCROLL** no se proporciona, el control de edición muestra tantas líneas posible y bip si se presiona ENTRAR cuando no queden líneas pueden mostrar.  Si se especifica el estilo de **ES\_AUTOHSCROLL** , el control de edición de varias líneas automáticamente se desplaza horizontalmente al símbolo de intercalación va más allá del borde derecho del control.  Para iniciar una nueva línea, el usuario deberá presionar ENTRAR.  Si **ES\_AUTOHSCROLL** no se proporciona, el control incluye automáticamente a palabras al principio de la línea siguiente cuando sea necesario; una nueva línea también se inicia si se presiona ENTRAR.  La posición de ajuste automático de línea está determinada por el tamaño de la ventana.  Si se vuelve a mostrar los cambios de tamaño de la ventana, la posición de ajuste automático de línea y el texto.  Los controles de edición de varias líneas pueden tener barras de desplazamiento.  Un control de edición con las barras de desplazamiento procesa sus propios mensajes de la barra de desplazamiento.  Los controles de edición sin barras de desplazamiento se mueven como se ha descrito anteriormente y procesan los mensajes de desplazamiento enviado por la ventana primaria.  
  
-   **ES\_NOHIDESEL** No, un control de edición oculta la selección cuando el control pierde el foco de entrada e invierte la selección cuando el control recibe el foco de entrada.  Especificando **ES\_NOHIDESEL** elimina esta acción predeterminado.  
  
-   Dígitos de**ES\_NUMBER**Allow sólo se entrarán en el control de edición.  
  
-   El texto de**ES\_OEMCONVERT**escribe en el control de edición se convierte de juego de caracteres ANSI el juego de caracteres OEM y de nuevo a ANSI.  Esto garantiza la conversión de caracteres adecuada cuando la aplicación llama a la función de `AnsiToOem` Windows para convertir una cadena ANSI en el control de edición en caracteres OEM.  Este estilo es muy útil para los controles de edición que contienen nombres de archivo.  
  
-   **ES\_PASSWORD** muestra todos los caracteres como un asterisco \(\#\#\#\*\) como se escriben en el control de edición.  Una aplicación puede utilizar la función miembro de `SetPasswordChar` para cambiar el carácter que se muestra.  
  
-   **ES\_READONLY** impide al usuario escribir o editar el texto del control de edición.  
  
-   **ES\_RIGHT** Derecho\- alinea el texto en un control de una línea o de edición de varias líneas.  
  
-   **ES\_UPPERCASE** convierte todos los caracteres en mayúsculas a medida que se escriben en el control de edición.  
  
-   **ES\_WANTRETURN** especifica que un retorno de carro está incrustado cuando el usuario presiona la tecla ENTRAR cuando escribe texto en un control de edición de varias líneas en un cuadro de diálogo.  Sin este estilo, presionar la tecla ENTRAR tiene el mismo efecto que a los cuadros de diálogo predeterminados el mismo botón.  Este estilo no tiene ningún efecto en un control de edición de una línea.  
  
## Vea también  
 [Estilos utilizados por MFC](../../mfc/reference/styles-used-by-mfc.md)   
 [CEdit::Create](../Topic/CEdit::Create.md)   
 [Edit Control Styles](http://msdn.microsoft.com/library/windows/desktop/bb775464)