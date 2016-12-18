---
title: "CStockPropImpl Class | Microsoft Docs"
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
  - "CStockPropImpl"
  - "ATL::CStockPropImpl"
  - "ATL.CStockPropImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles [ATL], propiedades estándar"
  - "CStockPropImpl class"
  - "propiedades estándar, controles ATL"
ms.assetid: 45f11d7d-6580-4a0e-872d-3bc8b836cfda
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CStockPropImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para admitir los valores de propiedad comunes.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template <  
class T,  
class InterfaceName,   
const IID* piid= &_ATL_IIDOF(InterfaceName),   
const GUID* plibid= &CComModule::m_libid,   
WORD wMajor= 1,  
WORD wMinor= 0,   
class tihclass= CcomTypeInfoHolder  
>  
class ATL_NO_VTABLE CStockPropImpl :  
public IDispatchImpl< InterfaceName, piid, plibid, wMajor,  
   wMinor, tihclass>  
```  
  
#### Parámetros  
 `T`  
 La clase que implementa el control y que deriva de `CStockPropImpl`.  
  
 `InterfaceName`  
 Una interfaz dual que expone las propiedades comunes.  
  
 `piid`  
 Un puntero al identificador IID de `InterfaceName`.  
  
 `plibid`  
 Un puntero al LIBID de la biblioteca de tipos que contiene la definición de `InterfaceName`.  
  
 `wMajor`  
 La versión principal de la biblioteca de tipos.  El valor predeterminado es 1.  
  
 `wMinor`  
 La versión secundaria de la biblioteca de tipos.  El valor predeterminado es 0.  
  
 `tihclass`  
 la clase utilizada para administrar la información de tipo para `T`.  El valor predeterminado es `CComTypeInfoHolder`.  
  
## Members  
  
### Métodos públicos  
  
|||  
|-|-|  
|[get\_Appearance](../Topic/CStockPropImpl::get_Appearance.md)|Llame a este método para obtener el estilo de dibujo utilizado por el control, por ejemplo, plano o 3D.|  
|[get\_AutoSize](../Topic/CStockPropImpl::get_AutoSize.md)|Llame a este método para obtener el estado de la marca que indica si el control no puede ser ningún otro tamaño.|  
|[get\_BackColor](../Topic/CStockPropImpl::get_BackColor.md)|Llame a este método para obtener el color de fondo del control.|  
|[get\_BackStyle](../Topic/CStockPropImpl::get_BackStyle.md)|Llame a este método para obtener el estilo de fondo del control, transparente u opaco.|  
|[get\_BorderColor](../Topic/CStockPropImpl::get_BorderColor.md)|Llame a este método para obtener el color del borde del control.|  
|[get\_BorderStyle](../Topic/CStockPropImpl::get_BorderStyle.md)|Llame a este método para obtener el estilo de borde del control.|  
|[get\_BorderVisible](../Topic/CStockPropImpl::get_BorderVisible.md)|Llame a este método para obtener el estado de la marca que indica si el borde del control está visible o no.|  
|[get\_BorderWidth](../Topic/CStockPropImpl::get_BorderWidth.md)|Llame a este método para obtener el ancho \(en píxeles\) del borde del control.|  
|[get\_Caption](../Topic/CStockPropImpl::get_Caption.md)|Llame a este método para obtener el texto especificado en la leyenda de un objeto.|  
|[get\_DrawMode](../Topic/CStockPropImpl::get_DrawMode.md)|Llame a este método para obtener el modo de gráfico del control, por ejemplo, lápiz XOR o para invertir los colores.|  
|[get\_DrawStyle](../Topic/CStockPropImpl::get_DrawStyle.md)|Llame a este método para obtener el estilo de dibujo del control, por ejemplo, sólido, rayados, o se punteó.|  
|[get\_DrawWidth](../Topic/CStockPropImpl::get_DrawWidth.md)|Llame a este método para obtener el ancho del gráfico \(en píxeles\) utilizado por los métodos de dibujo del control.|  
|[get\_Enabled](../Topic/CStockPropImpl::get_Enabled.md)|Llame a este método para obtener el estado de la marca que indica si se habilita el control.|  
|[get\_FillColor](../Topic/CStockPropImpl::get_FillColor.md)|Llame a este método para obtener el color de relleno del control.|  
|[get\_FillStyle](../Topic/CStockPropImpl::get_FillStyle.md)|Llame a este método para obtener el estilo de relleno del control, por ejemplo, sólido, transparentes, o lo marcó con rayitas cruzadas.|  
|[get\_Font](../Topic/CStockPropImpl::get_Font.md)|Llame a este método para obtener un puntero a las propiedades de fuente del control.|  
|[get\_ForeColor](../Topic/CStockPropImpl::get_ForeColor.md)|Llame a este método para obtener el color de primer plano del control.|  
|[get\_HWND](../Topic/CStockPropImpl::get_HWND.md)|Llame a este método para obtener el identificador de ventana asociado al control.|  
|[get\_MouseIcon](../Topic/CStockPropImpl::get_MouseIcon.md)|Llame a este método para obtener las propiedades de imagen del gráfico \(icono, un mapa de bits, o metarchivo\) que se va a mostrar cuando el mouse está sobre el control.|  
|[get\_MousePointer](../Topic/CStockPropImpl::get_MousePointer.md)|Llame a este método para obtener el tipo de puntero del mouse que aparece cuando el mouse está encima del control, por ejemplo, flecha, cruz, o reloj de arena.|  
|[get\_Picture](../Topic/CStockPropImpl::get_Picture.md)|Llame a este método para obtener un puntero a las propiedades de imágenes de un gráfico \(icono, un mapa de bits, o metarchivo\) que se va a mostrar.|  
|[get\_ReadyState](../Topic/CStockPropImpl::get_ReadyState.md)|Llame a este método para obtener el estado listo del control, por ejemplo, la carga o se ha cargado.|  
|[get\_TabStop](../Topic/CStockPropImpl::get_TabStop.md)|Llame a este método para obtener el mensaje que indica si el control es una tabulación o no.|  
|[get\_Text](../Topic/CStockPropImpl::get_Text.md)|Llame a este método para obtener el texto que se muestra con el control.|  
|[get\_Valid](../Topic/CStockPropImpl::get_Valid.md)|Llame a este método para obtener el estado de la marca que indica si el control es válido o no.|  
|[get\_Window](../Topic/CStockPropImpl::get_Window.md)|Llame a este método para obtener el identificador de ventana asociado al control.  idéntico a [CStockPropImpl:: get\_HWND](../Topic/CStockPropImpl::get_HWND.md).|  
|[put\_Appearance](../Topic/CStockPropImpl::put_Appearance.md)|Llame a este método para establecer el estilo de dibujo utilizado por el control, por ejemplo, plano o 3D.|  
|[put\_AutoSize](../Topic/CStockPropImpl::put_AutoSize.md)|Llame a este método para establecer el valor de marca que indica si el control no puede ser ningún otro tamaño.|  
|[put\_BackColor](../Topic/CStockPropImpl::put_BackColor.md)|Llame a este método para establecer el color de fondo del control.|  
|[put\_BackStyle](../Topic/CStockPropImpl::put_BackStyle.md)|Llame a este método para establecer el estilo de fondo del control.|  
|[put\_BorderColor](../Topic/CStockPropImpl::put_BorderColor.md)|Llame a este método para establecer el color del borde del control.|  
|[put\_BorderStyle](../Topic/CStockPropImpl::put_BorderStyle.md)|Llame a este método para establecer el estilo de borde del control.|  
|[put\_BorderVisible](../Topic/CStockPropImpl::put_BorderVisible.md)|Llame a este método para establecer el valor de marca que indica si el borde del control está visible o no.|  
|[put\_BorderWidth](../Topic/CStockPropImpl::put_BorderWidth.md)|Llame a este método para establecer el ancho del borde del control.|  
|[put\_Caption](../Topic/CStockPropImpl::put_Caption.md)|Llame a este método para establecer el texto que se mostrará al control.|  
|[put\_DrawMode](../Topic/CStockPropImpl::put_DrawMode.md)|Llame a este método para establecer el modo de gráfico del control, por ejemplo, lápiz XOR o para invertir los colores.|  
|[put\_DrawStyle](../Topic/CStockPropImpl::put_DrawStyle.md)|Llame a este método para establecer el estilo de dibujo del control, por ejemplo, sólido, discontinua, o se punteó.|  
|[put\_DrawWidth](../Topic/CStockPropImpl::put_DrawWidth.md)|Llame a este método para establecer el ancho \(en píxeles\) utilizado por los métodos de dibujo del control.|  
|[put\_Enabled](../Topic/CStockPropImpl::put_Enabled.md)|Llame a este método para establecer la marca que indica si se habilita el control.|  
|[put\_FillColor](../Topic/CStockPropImpl::put_FillColor.md)|Llame a este método para establecer el color de relleno del control.|  
|[put\_FillStyle](../Topic/CStockPropImpl::put_FillStyle.md)|Llame a este método para establecer el estilo de relleno del control, por ejemplo, sólido, transparentes, o lo marcó con rayitas cruzadas.|  
|[put\_Font](../Topic/CStockPropImpl::put_Font.md)|Llame a este método para establecer las propiedades de fuente del control.|  
|[put\_ForeColor](../Topic/CStockPropImpl::put_ForeColor.md)|Llame a este método para establecer el color de primer plano del control.|  
|[put\_HWND](../Topic/CStockPropImpl::put_HWND.md)|Este método devuelve E\_FAIL.|  
|[put\_MouseIcon](../Topic/CStockPropImpl::put_MouseIcon.md)|Llame a este método para establecer las propiedades de imagen del gráfico \(icono, un mapa de bits, o metarchivo\) que se va a mostrar cuando el mouse está sobre el control.|  
|[put\_MousePointer](../Topic/CStockPropImpl::put_MousePointer.md)|Llame a este método para establecer el tipo de puntero del mouse que aparece cuando el mouse está encima del control, por ejemplo, flecha, cruz, o reloj de arena.|  
|[put\_Picture](../Topic/CStockPropImpl::put_Picture.md)|Llame a este método para establecer las propiedades de imágenes de un gráfico \(icono, un mapa de bits, o metarchivo\) que se va a mostrar.|  
|[put\_ReadyState](../Topic/CStockPropImpl::put_ReadyState.md)|Llame a este método para establecer el estado listo del control, por ejemplo, la carga o se ha cargado.|  
|[put\_TabStop](../Topic/CStockPropImpl::put_TabStop.md)|Llame a este método para establecer el valor de marca que indica si el control es una tabulación o no.|  
|[put\_Text](../Topic/CStockPropImpl::put_Text.md)|Llame a este método para establecer el texto que se muestra con el control.|  
|[put\_Valid](../Topic/CStockPropImpl::put_Valid.md)|Llame a este método para establecer la marca que indica si el control es válido o no.|  
|[put\_Window](../Topic/CStockPropImpl::put_Window.md)|Este método llama a [CStockPropImpl::put\_HWND](../Topic/CStockPropImpl::put_HWND.md), que devuelve E\_FAIL.|  
|[putref\_Font](../Topic/CStockPropImpl::putref_Font.md)|Llame a este método para establecer las propiedades de fuente del control, con un recuento de referencia.|  
|[putref\_MouseIcon](../Topic/CStockPropImpl::putref_MouseIcon.md)|Llame a este método para establecer las propiedades de imagen del gráfico \(icono, un mapa de bits, o metarchivo\) que se va a mostrar cuando el mouse está sobre el control, con un recuento de referencia.|  
|[putref\_Picture](../Topic/CStockPropImpl::putref_Picture.md)|Llame a este método para establecer las propiedades de imágenes de un gráfico \(icono, un mapa de bits, o metarchivo\) que se mostrará, con un recuento de referencia.|  
  
## Comentarios  
 `CStockPropImpl` proporciona **put** y los métodos de **get** para cada almacenan la propiedad.  Estos métodos proporcionan el código necesario establecer u obtener el miembro de datos asociado a cada propiedad y notificarlo y sincronizarlo con el contenedor cuando cualquier cambio de propiedad.  
  
 Visual C\+\+ proporciona compatibilidad para las propiedades comunes a través de los asistentes.  Para obtener más información sobre las propiedades de la acción a un control, vea [tutorial de ATL](../../atl/active-template-library-atl-tutorial.md).  
  
 Por compatibilidad con versiones anteriores, `CStockPropImpl` también expone `get_Window` y los métodos de `put_Window` que llama simplemente `get_HWND` y `put_HWND`, respectivamente.  La implementación predeterminada de `put_HWND` devuelve **E\_FAIL** puesto que `HWND` debe ser una propiedad de sólo lectura.  
  
 Las propiedades siguientes también tienen una implementación de **putref** :  
  
-   Fuente  
  
-   MouseIcon  
  
-   Imagen  
  
 Las mismas tres propiedades comunes requieren su miembro de datos correspondiente ser de `CComPtr` tipo o de alguna otra clase que proporcione el recuento de referencias correcto de la interfaz mediante el operador de asignación.  
  
## Jerarquía de herencia  
 `T`  
  
 [IDispatchImpl](../../atl/reference/idispatchimpl-class.md)  
  
 `CStockPropImpl`  
  
## Requisitos  
 **encabezado:** atlctl.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)   
 [IDispatchImpl Class](../../atl/reference/idispatchimpl-class.md)