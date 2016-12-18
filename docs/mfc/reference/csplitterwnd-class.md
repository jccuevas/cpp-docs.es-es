---
title: "CSplitterWnd Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSplitterWnd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSplitterWnd class"
  - "dynamic splitter windows"
  - "varias vistas"
  - "ventanas divisoras"
  - "static splitter windows"
  - "vistas, varias por marco"
ms.assetid: fd0de258-6dbe-4552-9e47-a39de0471d51
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSplitterWnd Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la funcionalidad de una ventana divisora, que es una ventana que contiene varios paneles.  
  
## Sintaxis  
  
```  
class CSplitterWnd : public CWnd  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSplitterWnd::CSplitterWnd](../Topic/CSplitterWnd::CSplitterWnd.md)|Llame a para construir un objeto de `CSplitterWnd` .|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSplitterWnd::ActivateNext](../Topic/CSplitterWnd::ActivateNext.md)|Ejecuta el comando siguiente en el panel o el panel Anteriores de.|  
|[CSplitterWnd::CanActivateNext](../Topic/CSplitterWnd::CanActivateNext.md)|Comprueba si el comando siguiente en el panel o el panel Anteriores de es actualmente posible.|  
|[CSplitterWnd::Create](../Topic/CSplitterWnd::Create.md)|Llamada para crear una ventana y una publicación divisoras dinámicas en el objeto de `CSplitterWnd` .|  
|[CSplitterWnd::CreateScrollBarCtrl](../Topic/CSplitterWnd::CreateScrollBarCtrl.md)|crea un control de barra de desplazamiento compartido.|  
|[CSplitterWnd::CreateStatic](../Topic/CSplitterWnd::CreateStatic.md)|Llamada para crear una ventana y una publicación estáticas del divisor en el objeto de `CSplitterWnd` .|  
|[CSplitterWnd::CreateView](../Topic/CSplitterWnd::CreateView.md)|Llamada para crear un panel en una ventana divisora.|  
|[CSplitterWnd::DeleteColumn](../Topic/CSplitterWnd::DeleteColumn.md)|Elimina una columna de la ventana divisora.|  
|[CSplitterWnd::DeleteRow](../Topic/CSplitterWnd::DeleteRow.md)|Elimina una fila de la ventana divisora.|  
|[CSplitterWnd::DeleteView](../Topic/CSplitterWnd::DeleteView.md)|Elimina una vista en la ventana divisora.|  
|[CSplitterWnd::DoKeyboardSplit](../Topic/CSplitterWnd::DoKeyboardSplit.md)|Ejecuta el comando partido de teclado, normalmente “división ventana”.|  
|[CSplitterWnd::DoScroll](../Topic/CSplitterWnd::DoScroll.md)|Performs sincronizó el desplazamiento de ventanas divididas.|  
|[CSplitterWnd::DoScrollBy](../Topic/CSplitterWnd::DoScrollBy.md)|Desplaza las ventanas divididas por un número determinado de píxeles.|  
|[CSplitterWnd::GetActivePane](../Topic/CSplitterWnd::GetActivePane.md)|Determina el panel activo del foco o de la vista activa en el cuadro.|  
|[CSplitterWnd::GetColumnCount](../Topic/CSplitterWnd::GetColumnCount.md)|Devuelve el recuento actual de la columna del panel.|  
|[CSplitterWnd::GetColumnInfo](../Topic/CSplitterWnd::GetColumnInfo.md)|Devuelve la información de la columna especificada.|  
|[CSplitterWnd::GetPane](../Topic/CSplitterWnd::GetPane.md)|devuelve el panel en la fila y la columna especificadas.|  
|[CSplitterWnd::GetRowCount](../Topic/CSplitterWnd::GetRowCount.md)|Devuelve el número de filas actual del panel.|  
|[CSplitterWnd::GetRowInfo](../Topic/CSplitterWnd::GetRowInfo.md)|Devuelve la información de la fila especificada.|  
|[CSplitterWnd::GetScrollStyle](../Topic/CSplitterWnd::GetScrollStyle.md)|devuelve el estilo compartido de la barra de desplazamiento.|  
|[CSplitterWnd::IdFromRowCol](../Topic/CSplitterWnd::IdFromRowCol.md)|Devuelve el identificador de ventana secundaria del panel en la fila y la columna especificadas.|  
|[CSplitterWnd::IsChildPane](../Topic/CSplitterWnd::IsChildPane.md)|Llamada a determinar si la ventana está actualmente un panel secundario de esta ventana divisora.|  
|[CSplitterWnd::IsTracking](../Topic/CSplitterWnd::IsTracking.md)|Determina si la barra de división se mueve actualmente.|  
|[CSplitterWnd::RecalcLayout](../Topic/CSplitterWnd::RecalcLayout.md)|Llamada para redesplegar la ventana divisora después de ajustar la fila o el tamaño de columna.|  
|[CSplitterWnd::SetActivePane](../Topic/CSplitterWnd::SetActivePane.md)|Establece un panel sea el activo en el cuadro.|  
|[CSplitterWnd::SetColumnInfo](../Topic/CSplitterWnd::SetColumnInfo.md)|llamada para establecer la información especificada de la columna.|  
|[CSplitterWnd::SetRowInfo](../Topic/CSplitterWnd::SetRowInfo.md)|llamada para establecer la información especificada de la fila.|  
|[CSplitterWnd::SetScrollStyle](../Topic/CSplitterWnd::SetScrollStyle.md)|Especifica el nuevo estilo de la barra de desplazamiento para el uso compartido de la barra de desplazamiento de la ventana divisora.|  
|[CSplitterWnd::SplitColumn](../Topic/CSplitterWnd::SplitColumn.md)|Indica que una ventana de marco divide verticalmente.|  
|[CSplitterWnd::SplitRow](../Topic/CSplitterWnd::SplitRow.md)|Indica que una ventana de marco dividida horizontalmente.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSplitterWnd::OnDraw](../Topic/CSplitterWnd::OnDraw.md)|Llamado por el marco para dibujar la ventana divisora.|  
|[CSplitterWnd::OnDrawSplitter](../Topic/CSplitterWnd::OnDrawSplitter.md)|Representa una imagen de una ventana dividida.|  
|[CSplitterWnd::OnInvertTracker](../Topic/CSplitterWnd::OnInvertTracker.md)|Genera la imagen de una ventana dividida para ser del mismo taman\-o y la forma que la ventana de marco.|  
  
## Comentarios  
 Un panel normalmente es un objeto de aplicación concreto derivado de [CView](../../mfc/reference/cview-class.md), pero puede ser cualquier objeto de [CWnd](../../mfc/reference/cwnd-class.md) que tiene el identificador adecuada de la ventana secundaria  
  
 Un objeto de `CSplitterWnd` se inserta normalmente en un objeto primario de [CFrameWnd](../../mfc/reference/cframewnd-class.md) o de [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) .  Cree un objeto de `CSplitterWnd` mediante los pasos siguientes:  
  
1.  Inserte una variable miembro de `CSplitterWnd` en el cuadro primario.  
  
2.  Reemplace la función principal del miembro de [CFrameWnd:: OnCreateClient](../Topic/CFrameWnd::OnCreateClient.md) de marco.  
  
3.  Dentro de `OnCreateClient`invalidado, llame a funciones miembro de [Crear](../Topic/CSplitterWnd::Create.md) o de [CreateStatic](../Topic/CSplitterWnd::CreateStatic.md) de `CSplitterWnd`.  
  
 Llame a la función miembro de **Crear** para crear una ventana dinámica splitter.  Una ventana dinámica splitter se utiliza normalmente para crear y desplácese varios paneles individuales, o vistas, del mismo documento.  El marco de trabajo crea automáticamente un panel inicial del divisor; el marco de trabajo crea, el tamaño, y elimina de los paneles adicionales mientras el usuario funciona los controles de la ventana divisora.  
  
 Cuando se llama a **Crear**, especifica un alto de fila y el ancho de columna mínimos que determine cuándo los paneles son demasiado pequeños mostrar totalmente.  Después de llamar a **Crear**, puede ajustar estos mínimos llamando a [SetColumnInfo](../Topic/CSplitterWnd::SetColumnInfo.md) y el miembro de [SetRowInfo](../Topic/CSplitterWnd::SetRowInfo.md) funciona.  
  
 También use `SetColumnInfo` y el miembro de `SetRowInfo` funciona para establecer un ancho “ideal” para una columna y el alto “ideal” para una fila.  Cuando el marco muestra una ventana divisora, primero muestra el cuadro primario, la ventana divisora.  El marco después muestra los paneles en columnas y filas según sus dimensiones ideales, trabajando superior izquierda a la esquina inferior derecha del área de cliente de la ventana divisora.  
  
 Todos los paneles en una ventana dinámica splitter deben ser de la misma clase.  Las aplicaciones habituales que admiten las ventanas divisoras dinámicas incluyen Microsoft Word y Microsoft Excel.  
  
 Utilice la función miembro de `CreateStatic` para crear una ventana divisora estática.  El usuario sólo puede cambiar el tamaño de los paneles en una ventana divisora estática, no el número u orden.  
  
 Debe crear específicamente los paneles de todo el divisor estático cuando se crea el divisor estático.  Asegúrese de que crear todos los paneles antes de que la función principal del miembro de `OnCreateClient` de cuadro cambie, o marco no mostrará la ventana correctamente.  
  
 La función miembro de `CreateStatic` automáticamente inicializa un divisor estático con un alto de fila y el ancho de columna mínimos de 0.  Después de llamar a **Crear**, ajuste estos mínimos llamando a [SetColumnInfo](../Topic/CSplitterWnd::SetColumnInfo.md) y el miembro de [SetRowInfo](../Topic/CSplitterWnd::SetRowInfo.md) funciona.  También use `SetColumnInfo` y `SetRowInfo` después de llamar a `CreateStatic` para indicar dimensiones ideales deseadas del panel.  
  
 Paneles individuales de un divisor estático pertenecen a clases diferentes.  Para obtener ejemplos de las ventanas estáticas splitter, vea editor de gráficos y el administrador de archivos de Windows.  
  
 Una ventana divisora admite las barras de desplazamiento especiales \(aparte de las barras de desplazamiento que los paneles pueden tener\).  Estas barras de desplazamiento son elementos secundarios del objeto de `CSplitterWnd` y comparten con los paneles.  
  
 Cree estas barras de desplazamiento especiales al crear la ventana divisora.  Por ejemplo, `CSplitterWnd` que tiene una fila, dos columnas, y el estilo de **WS\_VSCROLL** mostrarán una barra de desplazamiento vertical que sea compartida por los dos paneles.  cuando el usuario mueve la barra de desplazamiento, los mensajes de `WM_VSCROLL` se envían a ambos paneles.  cuando los paneles establecen la posición de la barra de desplazamiento, se establece la barra de desplazamiento compartida.  
  
 Para obtener más información sobre las ventanas divisoras, vea:  
  
-   [nota técnica 29](../../mfc/tn029-splitter-windows.md)  
  
-   Caso Q262024 de Knowledge Base: HOWTO: uso CPropertySheet como elemento secundario de CSplitterWnd  
  
 Para obtener más información sobre cómo crear ventanas divisoras dinámicas, vea:  
  
-   ejemplo [Scribble](../../top/visual-cpp-samples.md)de MFC  
  
-   Ejemplo [VIEWEX](../../top/visual-cpp-samples.md)MFC.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSplitterWnd`  
  
## Requisitos  
 **encabezado:** afxext.h  
  
## Vea también  
 [ejemplo VIEWEX de MFC](../../top/visual-cpp-samples.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CView Class](../../mfc/reference/cview-class.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)