---
title: "CBitmapButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CBitmapButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mapas de bits, button controls"
  - "botones, mapa de bits"
  - "CBitmapButton class"
ms.assetid: 9ad6cb45-c3c4-4fb1-96d3-1fe3df7bbcfc
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CBitmapButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Crear controles de mismo botón etiquetados con imágenes trazadas un mapa de bits en lugar de texto.  
  
## Sintaxis  
  
```  
class CBitmapButton : public CButton  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CBitmapButton::CBitmapButton](../Topic/CBitmapButton::CBitmapButton.md)|Crea un objeto `CBitmapButton`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CBitmapButton::AutoLoad](../Topic/CBitmapButton::AutoLoad.md)|Asocia un botón en un cuadro de diálogo a un objeto de clase de `CBitmapButton` , carga los mapas de bits por nombre, y ajusta el botón para ajustar el mapa de bits.|  
|[CBitmapButton::LoadBitmaps](../Topic/CBitmapButton::LoadBitmaps.md)|Inicializa el objeto cargando uno o más recursos bitmap de archivo de recursos de la aplicación y asociar los mapas de bits al objeto.|  
|[CBitmapButton::SizeToContent](../Topic/CBitmapButton::SizeToContent.md)|Ajusta el botón para alojar el mapa de bits.|  
  
## Comentarios  
 los objetos de`CBitmapButton` contienen hasta cuatro mapas de bits, que contienen las imágenes en distintos estados que un botón puede suponer: encima de \(o normal\), abajo \(o seleccionado\), que tiene el foco, y deshabilitado.  Sólo se requiere el primer mapa de bits; los demás son opcionales.  
  
 las imágenes de Mapa de bits\-botón incluyen el borde alrededor de la imagen así como la imagen propio.  El borde hace normalmente una parte en mostrar el estado del botón.  Por ejemplo, el mapa de bits para el estado focused es normalmente como el del estado ascendente pero con una inserción de guiones del rectángulo de borde o una línea continua gruesa en el borde.  El mapa de bits para el estado deshabilitado se parece al que para el estado ascendente pero suele contraste inferior \(como una selección de menú atenuada o atenuada\).  
  
 Estos mapas de bits pueden tener cualquier tamaño, pero se tratan todos como si fueran el mismo tamaño que el mapa de bits para el estado ascendente.  
  
 Las diferentes aplicaciones exigen distintas combinaciones de imágenes de mapa de bits:  
  
|Flecha arriba|Verticalmente|Focused|Disabled|Application|  
|-------------------|-------------------|-------------|--------------|-----------------|  
|×||||Mapa de bits|  
|×|×|||botón sin el estilo de **WS\_TABSTOP**|  
|×|×|×|×|Botón de diálogo con todos estados|  
|×|×|×||Botón de diálogo con el estilo de **WS\_TABSTOP**|  
  
 Al crear un control de mapa de bits\-botón, establezca el estilo de **BS\_OWNERDRAW** para especificar que el botón propietario\-está dibujado.  Esto hace que Windows para enviar los mensajes de `WM_MEASUREITEM` y de `WM_DRAWITEM` para el botón; el marco controla estos mensajes y administra el aspecto del botón para usted.  
  
### Para crear un control de mapa de bits\-botón en el área cliente de una ventana  
  
1.  cree una a cuatro imágenes de mapa de bits para el botón.  
  
2.  Cree el objeto de [CBitmapButton](../Topic/CBitmapButton::CBitmapButton.md) .  
  
3.  Llame a la función de [Crear](../Topic/CButton::Create.md) para crear el control de botón de Windows y para adjuntarlo al objeto de `CBitmapButton` .  
  
4.  Llame a la función miembro de [LoadBitmaps](../Topic/CBitmapButton::LoadBitmaps.md) para cargar los recursos bitmap después de que se haya generado el botón bitmap.  
  
### Para incluir un control de mapa de bits\-botón en un cuadro de diálogo  
  
1.  cree una a cuatro imágenes de mapa de bits para el botón.  
  
2.  Cree una plantilla de cuadro de diálogo con un botón de dibujo propietario colocado donde desea que el botón bitmap.  El tamaño del botón en la plantilla no importa.  
  
3.  Establezca la leyenda del botón en un valor como “**MYIMAGE**” y define un símbolo para el botón como **IDC\_MYIMAGE**.  
  
4.  En el script de recursos de la aplicación, asigne cada una de las imágenes creadas para el botón un identificador construido anexando una de las letras “U”, “d”, “f”, o “X” \(hacia arriba, abajo, que tiene el foco, y deshabilitado\) a la cadena utilizada para la leyenda del botón en el paso 3.  Para la leyenda “**MYIMAGE**del botón”, por ejemplo, los id. sería “**MYIMAGEU**”, “**MYIMAGED**”, “**MYIMAGEF**,” y “**MYIMAGEX**.” Se **si es necesario** especifica el identificador de mapas de bits entre comillas dobles.  Si no el editor de recursos asignar un entero al recurso y MFC producirá un error al cargar la imagen.  
  
5.  En la clase de diálogo de la aplicación \(derivada de `CDialog`\), agregue un objeto miembro de `CBitmapButton` .  
  
6.  En la rutina de [OnInitDialog](../Topic/CDialog::OnInitDialog.md) del objeto de `CDialog` , llame a la función de [Autoload](../Topic/CBitmapButton::AutoLoad.md) del objeto de `CBitmapButton` , utilizando como parámetros el identificador del control de botón y el puntero de **this** del objeto de `CDialog` .  
  
 Si desea administrar los mensajes de notificación de Windows, como **BN\_CLICKED**, enviado por un control de mapa de bits\-botón a su elemento primario \(normalmente una clase derivada de **CDialog\)**, agrega a `CDialog`\- objeto derivado una función miembro de entrada y controlador de mensajes de mapa de mensajes para cada mensaje.  Las notificaciones enviadas por un objeto de `CBitmapButton` son iguales que las enviadas por un objeto de [CButton](../../mfc/reference/cbutton-class.md) .  
  
 La clase [CToolBar](../../mfc/reference/ctoolbar-class.md) toma un enfoque diferente para bitmap los botones.  
  
 Para obtener más información sobre `CBitmapButton`, vea[Controles](../../mfc/controls-mfc.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 `CBitmapButton`  
  
## Requisitos  
 **encabezado:** afxext.h  
  
## Vea también  
 [ejemplo CTRLTEST de MFC](../../top/visual-cpp-samples.md)   
 [CButton Class](../../mfc/reference/cbutton-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)