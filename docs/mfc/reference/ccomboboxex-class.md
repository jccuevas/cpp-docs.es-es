---
title: "CComboBoxEx Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComboBoxEx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComboBoxEx class"
  - "cuadros combinados [C++], CComboBoxEx class"
  - "common controls [C++], extended combo boxes"
  - "extended combo boxes, CComboBoxEx class"
  - "Internet Explorer 4.0 common controls"
  - "Windows common controls [C++], extended combo boxes"
ms.assetid: 33ca960a-2409-478c-84a4-a2ee8ecfe8f7
caps.latest.revision: 26
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComboBoxEx Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Extiende el control combobox proporcionar compatibilidad para las listas de imágenes.  
  
## Sintaxis  
  
```  
class CComboBoxEx : public CComboBox  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComboBoxEx::CComboBoxEx](../Topic/CComboBoxEx::CComboBoxEx.md)|Crea un objeto `CComboBoxEx`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComboBoxEx::Create](../Topic/CComboBoxEx::Create.md)|Crea el cuadro combinado y lo asocia al objeto de `CComboBoxEx` .|  
|[CComboBoxEx::CreateEx](../Topic/CComboBoxEx::CreateEx.md)|Crea un cuadro combinado con Windows especificado extendidas estilos y lo asocia a un objeto de **ComboBoxEx** .|  
|[CComboBoxEx::DeleteItem](../Topic/CComboBoxEx::DeleteItem.md)|quita un elemento de un control de **ComboBoxEx** .|  
|[CComboBoxEx::GetComboBoxCtrl](../Topic/CComboBoxEx::GetComboBoxCtrl.md)|Recupera un puntero al control secundario de cuadro combinado.|  
|[CComboBoxEx::GetEditCtrl](../Topic/CComboBoxEx::GetEditCtrl.md)|Recupera el identificador de la parte del control de edición de un control de **ComboBoxEx** .|  
|[CComboBoxEx::GetExtendedStyle](../Topic/CComboBoxEx::GetExtendedStyle.md)|Recupera los estilos extendidos que se utilizan para un control de **ComboBoxEx** .|  
|[CComboBoxEx::GetImageList](../Topic/CComboBoxEx::GetImageList.md)|Recupera un puntero a la lista de la imagen asignada a un control de **ComboBoxEx** .|  
|[CComboBoxEx::GetItem](../Topic/CComboBoxEx::GetItem.md)|Recupera información sobre el elemento para un elemento determinado de **ComboBoxEx** .|  
|[CComboBoxEx::HasEditChanged](../Topic/CComboBoxEx::HasEditChanged.md)|Determina si el usuario ha cambiado el contenido del control de edición **ComboBoxEx** escribiendo.|  
|[CComboBoxEx::InsertItem](../Topic/CComboBoxEx::InsertItem.md)|inserta un nuevo elemento en un control de **ComboBoxEx** .|  
|[CComboBoxEx::SetExtendedStyle](../Topic/CComboBoxEx::SetExtendedStyle.md)|Los conjuntos extendidas los estilos en un control de **ComboBoxEx** .|  
|[CComboBoxEx::SetImageList](../Topic/CComboBoxEx::SetImageList.md)|Establece una lista de imágenes para un control de **ComboBoxEx** .|  
|[CComboBoxEx::SetItem](../Topic/CComboBoxEx::SetItem.md)|Establece los atributos de un elemento en un control de **ComboBoxEx** .|  
|[CComboBoxEx::SetWindowTheme](../Topic/CComboBoxEx::SetWindowTheme.md)|Establece el estilo visual del control extendido de cuadro combinado.|  
  
## Comentarios  
 Mediante `CComboBoxEx` para crear los controles de cuadro combinado, ya no es necesario implementar su propio código de dibujo de la imagen.  En su lugar, utilice `CComboBoxEx` de tener acceso a imágenes de una imagen.  
  
## Compatibilidad con la lista de imágenes  
 En un cuadro combinado estándar, el propietario del cuadro combinado es responsable de dibujar una imagen creando el cuadro combinado como control de propietario\- dibujo.  Cuando se utiliza `CComboBoxEx`, no necesita establecer los estilos **CBS\_OWNERDRAWFIXED** y **CBS\_HASSTRINGS** de gráfico porque se implican.  Si no, debe escribir código para realizar operaciones de dibujo.  Un control de `CComboBoxEx` admite hasta tres imágenes por artículo: uno para un estado seleccionado, uno para un estado no seleccionada, y otro para una imagen de superposición.  
  
## Estilos  
 `CComboBoxEx` admite estilos **CBS\_SIMPLE**, **CBS\_DROPDOWN**, **CBS\_DROPDOWNLIST**, y **WS\_CHILD**.  El resto de los estilos pasados al crear la ventana omiten por el control.  Después de crear la ventana, puede proporcionar otros estilos de cuadro combinado llamando a la función [SetExtendedStyle](../Topic/CComboBoxEx::SetExtendedStyle.md)miembro de `CComboBoxEx` .  Con estos estilos, puede:  
  
-   Establezca las búsquedas de cadenas en la lista para distinguir entre mayúsculas y minúsculas.  
  
-   Cree un control de cuadro combinado que utiliza la barra diagonal \(“\/"\), barra diagonal inversa \(“\\ "\), y el punto \(“. "\) caracteres como delimitadores de word.  Esto permite que los usuarios omitan de palabra por palabra, mediante CTRL\+MAYÚS\+FLECHA de método abreviado de teclado CTRL\+.  
  
-   Establezca el control de cuadro combinado en la pantalla o no mostrar una imagen.  Si no se muestra ninguna imagen, el cuadro combinado se puede quitar la sangría de texto que contiene una imagen.  
  
-   Cree un control estrecho de cuadro combinado, incluida la clasificación de lo que recorta el cuadro combinado más ancho que contiene.  
  
 Estos marcadores de estilo se describen más detalladamente en [Mediante CComboBoxEx](../../mfc/using-ccomboboxex.md).  
  
## Elemento Retention y atributos del elemento Callback  
 Información sobre el elemento, como índices para los elementos y las imágenes, los valores de sangría, y las cadenas de texto, se almacena en la estructura [COMBOBOXEXITEM](http://msdn.microsoft.com/library/windows/desktop/bb775746)de Win32, como se describe en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  La estructura también contiene los miembros que corresponden a los marcadores de devolución de llamada.  
  
 Para obtener una explicación detallada, conceptual, vea [Mediante CComboBoxEx](../../mfc/using-ccomboboxex.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CComboBox](../../mfc/reference/ccombobox-class.md)  
  
 `CComboBoxEx`  
  
## Requisitos  
 **encabezado:** afxcmn.h  
  
## Vea también  
 [ejemplo MFCIE de MFC](../../top/visual-cpp-samples.md)   
 [CComboBox Class](../../mfc/reference/ccombobox-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CComboBox Class](../../mfc/reference/ccombobox-class.md)