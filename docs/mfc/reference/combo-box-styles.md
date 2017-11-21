---
title: Estilos de cuadro combinado | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CBS_LOWERCASE
- CBS_SORT
- CBS_OWNERDRAWVARIABLE
- CBS_OEMCONVERT
- CBS_AUTOHSCROLL
- CBS_NOINTEGRALHEIGHT
- CBS_SIMPLE
- CBS_DROPDOWNLIST
- CBS_DROPDOWN
- CBS_UPPERCASE
- CBS_HASSTRINGS
- CBS_DISABLENOSCROLL
- CBS_OWNERDRAWFIXED
dev_langs: C++
helpviewer_keywords:
- CBS_OWNERDRAWVARIABLE constant [MFC]
- CBS_NOINTEGRALHEIGHT constant [MFC]
- CBS_SIMPLE constant [MFC]
- CBS_AUTOHSCROLL constant [MFC]
- CBS_OEMCONVERT constant [MFC]
- CBS_DISABLENOSCROLL constant [MFC]
- CBS_HASSTRINGS constant [MFC]
- CBS_LOWERCASE constant [MFC]
- CBS_SORT constant [MFC]
- CBS_DROPDOWN constant [MFC]
- CBS_OWNERDRAWFIXED constant [MFC]
- combo boxes [MFC], styles
- CBS_UPPERCASE constant [MFC]
- CBS_DROPDOWNLIST constant
ms.assetid: d21a5023-e6a2-495b-a6bd-010a515cbc63
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 52cfd21df2f0f72da10589745fb3a8be3e0b24e1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="combo-box-styles"></a>Estilos de cuadro combinado
Los siguientes estilos de cuadro combinado están disponibles en MFC.  
  
-   **CBS_AUTOHSCROLL** Desplaza automáticamente el texto del control de edición hacia la derecha cuando el usuario escribe un carácter al final de la línea. Si no se establece este estilo, solo se permite el texto que entre dentro del límite rectangular.  
  
-   **CBS_DISABLENOSCROLL** El cuadro de lista muestra una barra de desplazamiento vertical deshabilitada si el cuadro de lista no contiene suficientes elementos por los que desplazarse. Sin este estilo, la barra de desplazamiento está oculta cuando el cuadro de lista no contiene suficientes elementos.  
  
-   **CBS_DROPDOWN** Similar a **CBS_SIMPLE**, salvo que el cuadro de lista no se muestra a menos que el usuario seleccione un icono junto al control de edición.  
  
-   **CBS_DROPDOWNLIST** Similar a **CBS_DROPDOWN**, salvo que el control de edición se reemplaza por un elemento de texto estático que muestra la selección actual del cuadro de lista.  
  
-   **CBS_HASSTRINGS** Un cuadro combinado dibujado por el propietario contiene elementos que se componen de cadenas. El cuadro combinado conserva la memoria y los punteros de las cadenas, de modo que la aplicación puede usar la función miembro `GetText` para recuperar el texto de un elemento determinado.  
  
-   **CBS_LOWERCASE** Pasa a minúsculas todo el texto tanto del campo de selección como de la lista.  
  
-   **CBS_NOINTEGRALHEIGHT** Especifica que el tamaño del cuadro combinado será exactamente igual al tamaño especificado por la aplicación cuando creó el cuadro combinado. Normalmente, Windows aplica un tamaño a los cuadros combinados que hace que estos no muestren elementos parciales.  
  
-   **CBS_OEMCONVERT** El texto escrito en el control de edición del cuadro combinado se convierte del juego de caracteres ANSI al juego de caracteres OEM y, de nuevo, a ANSI. Esto garantiza que los caracteres se van a convertir correctamente cuando la aplicación llame a la función `AnsiToOem` de Windows para convertir una cadena ANSI del cuadro combinado en caracteres OEM. Este estilo es de máxima utilidad en los cuadros combinados que contienen nombres de archivo y es válido únicamente para los cuadros combinados creados con los estilos **CBS_SIMPLE** o **CBS_DROPDOWN** .  
  
-   **CBS_OWNERDRAWFIXED** El propietario del cuadro de lista es responsable de dibujar su contenido. Los elementos del cuadro de lista tienen todos la misma altura.  
  
-   **CBS_OWNERDRAWVARIABLE** El propietario del cuadro de lista es responsable de dibujar su contenido. Los elementos del cuadro de lista tienen una altura variable.  
  
-   **CBS_SIMPLE** El cuadro de lista se muestra en todo momento. La selección actual del cuadro de lista se muestra en el control de edición.  
  
-   **CBS_SORT** Ordena automáticamente las cadenas especificadas en el cuadro de lista.  
  
-   **CBS_UPPERCASE** Pasa a mayúsculas todo el texto tanto del campo de selección como de la lista.  
  
## <a name="see-also"></a>Vea también  
 [Estilos utilizados por MFC](../../mfc/reference/styles-used-by-mfc.md)   
 [CComboBox::Create] (ccombobox class.md #ccombobox__create   



