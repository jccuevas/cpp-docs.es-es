---
title: Estilos de cuadro de lista | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LBS_STANDARD
- LBS_NODATA
- LBS_OWNERDRAWVARIABLE
- LBS_EXTENDEDSEL
- LBS_USETABSTOPS
- LBS_WANTKEYBOARDINPUT
- LBS_NOTIFY
- LBS_DISABLENOSCROLL
- LBS_HASSTRINGS
- LBS_NOREDRAW
- LBS_NOSEL
- LBS_NOINTEGRALHEIGHT
- LBS_MULTICOLUMN
- LBS_SORT
- LBS_MULTIPLESEL
- LBS_OWNERDRAWFIXED
dev_langs: C++
helpviewer_keywords:
- LBS_NOSEL constant [MFC]
- LBS_NOREDRAW constant [MFC]
- LBS_HASSTRINGS constant [MFC]
- LBS_OWNERDRAWFIXED constant [MFC]
- LBS_WANTKEYBOARDINPUT constant [MFC]
- LBS_STANDARD constant [MFC]
- LBS_MULTIPLESEL constant [MFC]
- LBS_OWNERDRAWVARIABLE constant [MFC]
- LBS_DISABLENOSCROLL constant [MFC]
- LBS_NODATA constant [MFC]
- list boxes [MFC], styles
- LBS_EXTENDEDSEL constant [MFC]
- LBS_MULTICOLUMN constant [MFC]
- LBS_NOTIFY constant [MFC]
- LBS_USETABSTOPS constant [MFC]
- LBS_NOINTEGRALHEIGHT constant [MFC]
- LBS_SORT constant
ms.assetid: 3f357b8d-9118-4f41-9e28-02ed92d1e88f
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8f52734e26d1965811aded67bc1e1dde6a2c28bc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="list-box-styles"></a>Estilos de cuadro de lista
-   **LBS_DISABLENOSCROLL** el cuadro de lista muestra una barra cuando el cuadro de lista no contiene suficientes elementos para desplazarse de deshabilitado desplazamiento vertical. Sin este estilo, la barra de desplazamiento está oculta cuando el cuadro de lista no contiene suficientes elementos.  
  
-   **LBS_EXTENDEDSEL** el usuario puede seleccionar varios elementos con la tecla MAYÚS y el mouse (ratón) o combinaciones de teclas especiales.  
  
-   **LBS_HASSTRINGS** especifica un cuadro de lista dibujado por el propietario que contiene elementos que se componen de cadenas. El cuadro de lista mantiene la memoria y los punteros de las cadenas, por lo que la aplicación puede utilizar el `GetText` función miembro para recuperar el texto de un elemento determinado.  
  
-   **LBS_MULTICOLUMN** especifica un cuadro de lista de varias columnas que se desplaza horizontalmente. El `SetColumnWidth` función miembro establece el ancho de las columnas.  
  
-   **LBS_MULTIPLESEL** selección de la cadena se muestra o cada vez que el usuario hace clic o doble clic en la cadena. Puede seleccionar cualquier número de cadenas.  
  
-   **LBS_NODATA** especifica un cuadro de lista sin datos. Especifique este estilo cuando el número de elementos en el cuadro de lista será superior a mil. Un cuadro de lista de datos no debe tener la **LBS_OWNERDRAWFIXED** de estilo, pero no debe tener la **LBS_SORT** o **LBS_HASSTRINGS** estilo.  
  
     Un cuadro de lista de datos no es similar a un cuadro de lista dibujado por el propietario, salvo que no contiene datos para un elemento de cadena o mapa de bits. Comandos para agregar, insertar o eliminar un elemento lleve a cabo omitirá cualquier elemento de datos; solicitudes de búsqueda de una cadena en el cuadro de lista siempre se producirá un error. El sistema envía el `WM_DRAWITEM` mensaje en la ventana de propietario cuando se debe dibujar un elemento. El miembro itemID de la `DRAWITEMSTRUCT` estructura pasa con el `WM_DRAWITEM` mensaje especifica el número de línea del elemento que se va a dibujar. Un cuadro de lista sin datos no envía un `WM_DELETEITEM` mensaje.  
  
-   **LBS_NOINTEGRALHEIGHT** el tamaño del cuadro de lista es exactamente el tamaño especificado por la aplicación cuando crea el cuadro de lista. Normalmente, Windows cambia el tamaño de un cuadro de lista para que el cuadro de lista no muestren elementos parciales.  
  
-   **LBS_NOREDRAW** presentación del cuadro de lista no se actualiza cuando se realizan cambios. Este estilo se puede cambiar en cualquier momento mediante el envío de un **WM_SETREDRAW** mensaje.  
  
-   **LBS_NOSEL** especifica que el cuadro de lista contiene los elementos que se pueden ver pero no seleccionados.  
  
-   **LBS_NOTIFY** ventana primaria recibe un mensaje de entrada cada vez que el usuario hace clic o doble clic en una cadena.  
  
-   **LBS_OWNERDRAWFIXED** el propietario del cuadro de lista es responsable de dibujar su contenido; los elementos en el cuadro de lista tienen el mismo alto.  
  
-   **LBS_OWNERDRAWVARIABLE** el propietario del cuadro de lista es responsable de dibujar su contenido; los elementos en el cuadro de lista son variables de alto.  
  
-   **LBS_SORT** cadenas en el cuadro de lista se ordenan alfabéticamente.  
  
-   **LBS_STANDARD** cadenas en el cuadro de lista se ordenan alfabéticamente y la ventana primaria recibe un mensaje de entrada cada vez que el usuario hace clic o doble clic en una cadena. El cuadro de lista contiene bordes en todos los lados.  
  
-   **LBS_USETABSTOPS** permite un cuadro de lista reconozca y expanda los caracteres de tabulación al dibujar sus cadenas. Las posiciones de tabulación predeterminada son 32 unidades de cuadro de diálogo. (Una unidad de cuadro de diálogo es una distancia horizontal o vertical. Una unidad de cuadro de diálogo horizontal equivale a una cuarta parte de la unidad de base de ancho del cuadro de diálogo actual. Las unidades de base del cuadro de diálogo se calculan basándose en el alto y ancho de la fuente del sistema actual. El **GetDialogBaseUnits** la función de Windows devuelve el cuadro de diálogo actual unidades base en píxeles.) Este estilo no debe usarse con **LBS_OWNERDRAWFIXED**.  
  
-   **LBS_WANTKEYBOARDINPUT** recibe el propietario del cuadro de lista `WM_VKEYTOITEM` o `WM_CHARTOITEM` mensajes cada vez que el usuario presiona una tecla mientras el cuadro de lista tiene foco de entrada. Esto permite que una aplicación realizar un procesamiento especial en la entrada del teclado.  
  
## <a name="see-also"></a>Vea también  
 [Estilos utilizados por MFC](../../mfc/reference/styles-used-by-mfc.md)   
 [CListBox::Create](../../mfc/reference/clistbox-class.md#create)   
 [Estilos de cuadro de lista](http://msdn.microsoft.com/library/windows/desktop/bb775149)

