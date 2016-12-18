---
title: "CImageList Class | Microsoft Docs"
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
  - "CImageList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CImageList class"
  - "image lists [C++], CImageList class"
  - "Windows common controls [C++], CImageList"
ms.assetid: b6d1a704-1c82-4548-8a8f-77972adc98a5
caps.latest.revision: 19
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CImageList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la funcionalidad del control de lista común de imágenes de Windows.  
  
## Sintaxis  
  
```  
class CImageList : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CImageList::CImageList](../Topic/CImageList::CImageList.md)|Crea un objeto `CImageList`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CImageList::Add](../Topic/CImageList::Add.md)|Agrega una imagen o imágenes a una lista de imágenes.|  
|[CImageList::Attach](../Topic/CImageList::Attach.md)|Adjunta una imagen orden a un objeto de `CImageList` .|  
|[CImageList::BeginDrag](../Topic/CImageList::BeginDrag.md)|Comienza que arrastre una imagen.|  
|[CImageList::Copy](../Topic/CImageList::Copy.md)|copia una imagen dentro de un objeto de `CImageList` .|  
|[CImageList::Create](../Topic/CImageList::Create.md)|Inicializa una imagen lista y lo asocia a un objeto de `CImageList` .|  
|[CImageList::DeleteImageList](../Topic/CImageList::DeleteImageList.md)|Elimina una lista de imágenes.|  
|[CImageList::DeleteTempMap](../Topic/CImageList::DeleteTempMap.md)|Invoca el controlador de tiempo de inactividad de [CWinApp](../../mfc/reference/cwinapp-class.md) para eliminar cualquier objeto temporal de `CImageList` creado por `FromHandle`.|  
|[CImageList::Detach](../Topic/CImageList::Detach.md)|Desasocia un objeto de la lista de imágenes de un objeto de `CImageList` y devuelve un identificador a una lista de imágenes.|  
|[CImageList::DragEnter](../Topic/CImageList::DragEnter.md)|Bloqueos actualizaciones durante una operación de arrastre y muestra la imagen de arrastre en una posición especificada.|  
|[CImageList::DragLeave](../Topic/CImageList::DragLeave.md)|Desbloquea la ventana y oculta la imagen de arrastre para poder actualizar la ventana.|  
|[CImageList::DragMove](../Topic/CImageList::DragMove.md)|Mueve la imagen que se arrastra durante una operación de arrastrar y colocar.|  
|[CImageList::DragShowNolock](../Topic/CImageList::DragShowNolock.md)|Muestra u oculta la imagen de arrastre durante una operación de arrastre, sin bloquear la ventana.|  
|[CImageList::Draw](../Topic/CImageList::Draw.md)|Dibuja la imagen que se arrastra durante una operación de arrastrar y colocar.|  
|[CImageList::DrawEx](../Topic/CImageList::DrawEx.md)|Dibuja un elemento de lista de la imagen en el contexto especificado del dispositivo.  La función utiliza el estilo de dibujo especificado y combinación la imagen con el color especificado.|  
|[CImageList::DrawIndirect](../Topic/CImageList::DrawIndirect.md)|Dibuja una imagen de una imagen.|  
|[CImageList::EndDrag](../Topic/CImageList::EndDrag.md)|Finaliza una operación de arrastre.|  
|[CImageList::ExtractIcon](../Topic/CImageList::ExtractIcon.md)|Crea un icono basado en una imagen y una máscara en una lista de imágenes.|  
|[CImageList::FromHandle](../Topic/CImageList::FromHandle.md)|Devuelve un puntero a un objeto de `CImageList` cuando se le asigna un identificador a una lista de imágenes.  Si un objeto de `CImageList` no se asocia al identificador, se crea y se adjunta un objeto temporal de `CImageList` .|  
|[CImageList::FromHandlePermanent](../Topic/CImageList::FromHandlePermanent.md)|Devuelve un puntero a un objeto de `CImageList` cuando se le asigna un identificador a una lista de imágenes.  Si un objeto de `CImageList` no se asocia al identificador, se devuelve **NULL** .|  
|[CImageList::GetBkColor](../Topic/CImageList::GetBkColor.md)|Recupera el color de fondo actual una lista de imágenes.|  
|[CImageList::GetDragImage](../Topic/CImageList::GetDragImage.md)|Obtiene la imagen temporal indicado que se utiliza para arrastrar.|  
|[CImageList::GetImageCount](../Topic/CImageList::GetImageCount.md)|Recupera el número de imágenes en una lista de imágenes.|  
|[CImageList::GetImageInfo](../Topic/CImageList::GetImageInfo.md)|Recupera información sobre una imagen.|  
|[CImageList::GetSafeHandle](../Topic/CImageList::GetSafeHandle.md)|recupera **m\_hImageList**.|  
|[CImageList::Read](../Topic/CImageList::Read.md)|Lee una imagen lista de un archivo.|  
|[CImageList::Remove](../Topic/CImageList::Remove.md)|Quita una imagen de una imagen.|  
|[CImageList::Replace](../Topic/CImageList::Replace.md)|Reemplaza una imagen en una imagen que aparece con una nueva imagen.|  
|[CImageList::SetBkColor](../Topic/CImageList::SetBkColor.md)|Establece el color de fondo para una lista de imágenes.|  
|[CImageList::SetDragCursorImage](../Topic/CImageList::SetDragCursorImage.md)|Crea una nueva imagen de arrastre.|  
|[CImageList::SetImageCount](../Topic/CImageList::SetImageCount.md)|Restablece el recuento de imágenes en una lista de imágenes.|  
|[CImageList::SetOverlayImage](../Topic/CImageList::SetOverlayImage.md)|Agrega el índice de base cero de una imagen a la lista de imágenes que se van a utilizar como máscaras de superposición.|  
|[CImageList::Write](../Topic/CImageList::Write.md)|Escribe una imagen de un archivo.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CImageList::operator HIMAGELIST](../Topic/CImageList::operator%20HIMAGELIST.md)|Devuelve `HIMAGELIST` asociado a `CImageList`.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CImageList::m\_hImageList](../Topic/CImageList::m_hImageList.md)|Un identificador que contiene la lista de la imagen asociada a este objeto.|  
  
## Comentarios  
 Una “imagen lista” es una colección de imágenes mismo\-clasificadas, que se pueden hacer referencia por su índice de base cero.  Las listas de imágenes se utilizan para administrar eficazmente conjuntos grandes de iconos o de mapas de bits.  Todas las imágenes en una lista de imágenes contenidas en un mapa de bits único, ancho en formato de dispositivo de pantalla.  Una lista de imágenes también puede incluir un mapa de bits monocromo que contiene las máscaras utilizadas para dibujar imágenes transparente \(estilo de icono\).  La interfaz de programación de aplicaciones Win32 de \(API\) Microsoft proporciona la lista de imágenes funciones que permiten dibujar imágenes, crear o destruir listas de imágenes, para agregar y quitar imágenes, para reemplazar imágenes, para combinar, imágenes y para arrastrar imágenes.  
  
 Este control \(y por consiguiente la clase de `CImageList` \) sólo está disponible para los programas que se ejecutan en versión 3,51 de Windows 95 \/98 y Windows NT y posterior.  
  
 Para obtener más información sobre cómo utilizar `CImageList`, vea [Controles](../../mfc/controls-mfc.md) y [Mediante CImageList](../../mfc/using-cimagelist.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CImageList`  
  
## Requisitos  
 **encabezado:** afxcmn.h  
  
## Vea también  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CListCtrl Class](../../mfc/reference/clistctrl-class.md)   
 [CTabCtrl Class](../../mfc/reference/ctabctrl-class.md)