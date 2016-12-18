---
title: "CAnimateCtrl Class | Microsoft Docs"
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
  - "CAnimateCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "animation controls [C++], CAnimateCtrl class"
  - "CAnimateCtrl class"
  - "Windows common controls [C++], CAnimateCtrl class"
ms.assetid: 5e8eb1bd-96b7-47b8-8de2-6bcbb3cc299b
caps.latest.revision: 25
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAnimateCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la funcionalidad del control común de animación de Windows.  
  
## Sintaxis  
  
```  
  
class CAnimateCtrl : public CWnd  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimateCtrl::CAnimateCtrl](../Topic/CAnimateCtrl::CAnimateCtrl.md)|Crea un objeto `CAnimateCtrl`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimateCtrl::Close](../Topic/CAnimateCtrl::Close.md)|Cierre AVI recorte.|  
|[CAnimateCtrl::Create](../Topic/CAnimateCtrl::Create.md)|Crea un control de animación y lo asocia a un objeto de `CAnimateCtrl` .|  
|[CAnimateCtrl::CreateEx](../Topic/CAnimateCtrl::CreateEx.md)|Crea un control de animación con Windows especificado extendidas estilos y lo asocia a un objeto de `CAnimateCtrl` .|  
|[CAnimateCtrl::IsPlaying](../Topic/CAnimateCtrl::IsPlaying.md)|Indica si un formato AVI \(AVI\) recorte se está reproduciendo.|  
|[CAnimateCtrl::Open](../Topic/CAnimateCtrl::Open.md)|Abra AVI clip de un archivo o un recurso y muestra el primer cuadro.|  
|[CAnimateCtrl::Play](../Topic/CAnimateCtrl::Play.md)|Reproduce AVI recorte sin sonido.|  
|[CAnimateCtrl::Seek](../Topic/CAnimateCtrl::Seek.md)|Muestra un único cuadro seleccionado de AVI recorte.|  
|[CAnimateCtrl::Stop](../Topic/CAnimateCtrl::Stop.md)|Detiene la reproducción de AVI recorte.|  
  
## Comentarios  
 Este control \(y por consiguiente la clase de `CAnimateCtrl` \) sólo está disponible para los programas que se ejecutan en versión 3,51 de Windows 95, Windows 98, y Windows NT y posterior.  
  
 Un control de la animación es una ventana rectangular que muestra clip en formato de AVI \(formato AVI\) el vídeo y el formato de audio estándar de Windows.  AVI recorte es ejecuciones de marcos bitmap, como una película.  
  
 Los controles de animación pueden reproducir sólo los fragmentos simples de AVI.  Específicamente, los fragmentos que se según por un control de animación deben cumplir los siguientes requisitos:  
  
-   Debe haber exactamente una transmisión de vídeo y al menos un cuadro.  
  
-   Puede haber a lo sumo dos secuencias en el archivo \(normalmente la otra secuencia, si está presente, es una secuencia audio, aunque el control de animación omita información de audio\).  
  
-   Recorte debe ser sin comprimir o comprimido con la compresión RLE8.  
  
-   No se permite ningún cambio en la paleta de la transmisión de vídeo.  
  
 Puede agregar AVI recorte a su aplicación como recurso de AVI, o puede adjuntar la aplicación como archivo AVI independiente.  
  
 Porque su subproceso continúa ejecutándose mientras se muestra AVI recorte, un uso común de un control de la animación es indicar la actividad del sistema durante una operación larga.  Por ejemplo, el cuadro de diálogo de búsqueda del Explorador de archivos muestra una lupa móvil como las búsquedas del sistema para un archivo.  
  
 Si crea un objeto de `CAnimateCtrl` dentro de un cuadro de diálogo o un recurso de cuadro de diálogo mediante el editor de cuadros de diálogo, automáticamente se destruirá cuando el usuario cierra el cuadro de diálogo.  
  
 Si crea un objeto de `CAnimateCtrl` dentro de una ventana, puede necesitar destruirla.  Si crea el objeto de `CAnimateCtrl` en la pila, se destruye automáticamente.  Si crea el objeto de `CAnimateCtrl` en la pila mediante la función de **nuevo** , debe llamar a **borrar** en el objeto para destruirlo.  Si deriva una nueva clase de `CAnimateCtrl` y asigna cualquier memoria en esta clase, invalide `CAnimateCtrl` destructor para destruyen las asignaciones.  
  
 Para obtener más información sobre cómo utilizar `CAnimateCtrl`, vea [Controles](../../mfc/controls-mfc.md) y [Mediante CAnimateCtrl](../../mfc/using-canimatectrl.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CAnimateCtrl`  
  
## Requisitos  
 **encabezado:** afxcmn.h  
  
## Vea también  
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CAnimateCtrl::Create](../Topic/CAnimateCtrl::Create.md)   
 [ON\_CONTROL](../Topic/ON_CONTROL.md)