---
title: CMetaFileDC (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMetaFileDC
- AFXEXT/CMetaFileDC
- AFXEXT/CMetaFileDC::CMetaFileDC
- AFXEXT/CMetaFileDC::Close
- AFXEXT/CMetaFileDC::CloseEnhanced
- AFXEXT/CMetaFileDC::Create
- AFXEXT/CMetaFileDC::CreateEnhanced
dev_langs:
- C++
helpviewer_keywords:
- CMetaFileDC [MFC], CMetaFileDC
- CMetaFileDC [MFC], Close
- CMetaFileDC [MFC], CloseEnhanced
- CMetaFileDC [MFC], Create
- CMetaFileDC [MFC], CreateEnhanced
ms.assetid: ffce60fa-4181-4d46-9832-25e46fad4db4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8bb903bb38194be5b6a72f27ed683e965d7605b4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cmetafiledc-class"></a>CMetaFileDC (clase)
Implementa un metarchivo de Windows, que contiene una secuencia de comandos de la interfaz de dispositivo gráfico (GDI) que puede volver a consultar para crear la imagen o el texto que desee.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMetaFileDC : public CDC  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMetaFileDC::CMetaFileDC](#cmetafiledc)|Construye un objeto `CMetaFileDC`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMetaFileDC::Close](#close)|Cierra el contexto de dispositivo y crea un identificador de metarchivo.|  
|[CMetaFileDC::CloseEnhanced](#closeenhanced)|Cierra un contexto de dispositivo de metarchivo mejorado y crea un identificador de metarchivo mejorado.|  
|[CMetaFileDC::Create](#create)|Crea el contexto de dispositivo de metarchivo de Windows y lo adjunta a la `CMetaFileDC` objeto.|  
|[CMetaFileDC::CreateEnhanced](#createenhanced)|Crea un contexto de dispositivo de metarchivo para un metarchivo de formato mejorado.|  
  
## <a name="remarks"></a>Comentarios  
 Para implementar un metarchivo de Windows, cree primero un `CMetaFileDC` objeto. Invocar la `CMetaFileDC` constructor, a continuación, llame a la [crear](#create) función de miembro, que crea un contexto de dispositivo de metarchivo de Windows y lo adjunta a la `CMetaFileDC` objeto.  
  
 Después de enviar el `CMetaFileDC` objeto de la secuencia de `CDC` comandos GDI que se va a reproducir que. Solo los comandos GDI que crean como resultado, `MoveTo` y `LineTo`, se puede utilizar.  
  
 Después de enviar los comandos que desee en el metarchivo, llame a la **cerrar** función de miembro, que cierra los contextos de dispositivo de metarchivo y devuelve un identificador de metarchivo. A continuación, eliminar el `CMetaFileDC` objeto.  
  
 [CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile) , a continuación, se puede usar el identificador del metarchivo para reproducir el metarchivo varias veces. Metarchivo también se puede manipular con funciones de Windows como [CopyMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183480), que copia un metarchivo en el disco.  
  
 Cuando ya no se necesita el metarchivo, eliminarlo de la memoria con el [DeleteMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183537) la función de Windows.  
  
 También puede implementar la `CMetaFileDC` objeto por lo que puede controlar las llamadas de salida y atributo GDI llama como `GetTextExtent`. Un metarchivo de este tipo es más flexible y pueden más fácilmente reutilizar código GDI general, que a menudo se compone de una combinación de llamadas de salida y atributo. El `CMetaFileDC` clase hereda de dos contextos de dispositivo, `m_hDC` y `m_hAttribDC`, de `CDC`. El `m_hDC` contexto de dispositivo encarga de toda [CDC](../../mfc/reference/cdc-class.md) GDI llamadas de salida y la `m_hAttribDC` contexto de dispositivo encarga de toda `CDC` llamadas de atributo GDI. Normalmente, estos contextos de dos dispositivo hacen referencia al mismo dispositivo. En el caso de `CMetaFileDC`, el controlador de dominio está establecido en **NULL** de forma predeterminada.  
  
 Crear un segundo contexto de dispositivo que apunta a la pantalla, una impresora o dispositivo que no sea un metarchivo, a continuación, llame a la `SetAttribDC` función de miembro para asociar el nuevo contexto de dispositivo con `m_hAttribDC`. Llamadas GDI para obtener información ahora se dirigirá a la nueva `m_hAttribDC`. Llamadas GDI de salida será dirigido a `m_hDC`, que representa el metarchivo.  
  
 Para obtener más información sobre `CMetaFileDC`, consulte [contextos de dispositivo](../../mfc/device-contexts.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CMetaFileDC`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxext.h  
  
##  <a name="close"></a>CMetaFileDC::Close  
 Cierra el contexto de dispositivo de metarchivo y crea un identificador de metarchivo de Windows que puede usarse para reproducir el metarchivo mediante la [CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile) función miembro.  
  
```  
HMETAFILE Close();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Válido **HMETAFILE** si la función se realiza correctamente; en caso contrario **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 El identificador del metarchivo de Windows también puede utilizarse para manipular el metarchivo con funciones de Windows como [CopyMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183480).  
  
 Eliminar el metarchivo tras su uso mediante una llamada a las ventanas [DeleteMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183537) (función).  
  
##  <a name="closeenhanced"></a>CMetaFileDC::CloseEnhanced  
 Cierra un contexto de dispositivo de metarchivo mejorado y devuelve un identificador que identifica un metarchivo con formato mejorado.  
  
```  
HENHMETAFILE CloseEnhanced();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador de un metarchivo mejorado, si se realiza correctamente; en caso contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Una aplicación puede utilizar el identificador de metarchivo mejorado devuelto por esta función para realizar las siguientes tareas:  
  
-   Mostrar una imagen almacenada en un metarchivo mejorado  
  
-   Crear copias del metarchivo mejorado  
  
-   Enumerar, editar o copiar registros individuales del metarchivo mejorado  
  
-   Recuperar una descripción opcional del contenido del metarchivo desde el encabezado de metarchivo mejorado  
  
-   Recupere una copia del encabezado del metarchivo mejorado  
  
-   Recuperar una copia binaria del metarchivo mejorado  
  
-   Enumerar los colores de la paleta opcional  
  
-   Convertir un metarchivo con formato mejorado en un metarchivo de formato de Windows  
  
 Cuando la aplicación ya no necesita el identificador del metarchivo mejorado, debe liberar el identificador mediante una llamada a Win32 **DeleteEnhMetaFile** función.  
  
##  <a name="cmetafiledc"></a>CMetaFileDC::CMetaFileDC  
 Construir un `CMetaFileDC` objeto en dos pasos.  
  
```  
CMetaFileDC();
```  
  
### <a name="remarks"></a>Comentarios  
 En primer lugar, llame a `CMetaFileDC`, a continuación, llame a **crear**, que crea el contexto de dispositivo de metarchivo de Windows y lo adjunta a la `CMetaFileDC` objeto.  
  
##  <a name="create"></a>CMetaFileDC::Create  
 Construir un `CMetaFileDC` objeto en dos pasos.  
  
```  
BOOL Create(LPCTSTR lpszFilename = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszFilename*  
 Apunta a una cadena de caracteres terminadas en null. Especifica el nombre de archivo del metarchivo que se va a crear. Si *lpszFilename* es **NULL**, se crea un nuevo metarchivo en memoria.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 En primer lugar, llame al constructor de `CMetaFileDC`, a continuación, llame a **crear**, que crea el contexto de dispositivo de metarchivo de Windows y lo adjunta a la `CMetaFileDC` objeto.  
  
##  <a name="createenhanced"></a>CMetaFileDC::CreateEnhanced  
 Crea un contexto de dispositivo para un metarchivo de formato mejorado.  
  
```  
BOOL CreateEnhanced(
    CDC* pDCRef,  
    LPCTSTR lpszFileName,  
    LPCRECT lpBounds,  
    LPCTSTR lpszDescription);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDCRef`  
 Identifica un dispositivo de referencia para el metarchivo mejorado.  
  
 `lpszFileName`  
 Apunta a una cadena de caracteres terminadas en null. Especifica el nombre de archivo para el metarchivo mejorado al crearse. Si este parámetro es **NULL**, metarchivo mejorado está basada en memoria y su contenido que se pierde cuando se destruye el objeto o cuando el Win32 **DeleteEnhMetaFile** función se invoca.  
  
 `lpBounds`  
 Apunta a un [RECT](../../mfc/reference/rect-structure1.md) estructura de datos o un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que especifica las dimensiones de **HIMETRIC** unidades (en incrementos de milímetro.01) de la imagen que se almacenará en el Metarchivo mejorado.  
  
 `lpszDescription`  
 Apunta a una cadena terminada en cero que especifica el nombre de la aplicación que creó la imagen, así como el título de la imagen.  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador del contexto de dispositivo de metarchivo mejorado, si se realiza correctamente; en caso contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Este controlador de dominio puede utilizarse para almacenar una imagen independiente del dispositivo.  
  
 Windows usa el dispositivo de referencia identificado por el `pDCRef` parámetro para registrar la resolución y las unidades del dispositivo en el que aparecieron una imagen. Si el `pDCRef` parámetro es **NULL**, que utiliza el dispositivo de presentación actual como referencia.  
  
 Los miembros de la izquierda y superiores de la `RECT` estructura de datos que señala el `lpBounds` parámetro debe ser menor que los miembros derecho e inferior, respectivamente. Puntos a lo largo de los bordes del rectángulo se incluyen en la imagen. Si `lpBounds` es **NULL**, la interfaz de dispositivo gráfico (GDI) calcula las dimensiones del rectángulo más pequeño que puede incluir la imagen dibujada por la aplicación. El `lpBounds` parámetro debe especificarse siempre que sea posible.  
  
 La cadena que señala el `lpszDescription` parámetro debe contener un carácter null entre el nombre de la aplicación y el nombre de imagen y debe terminar con dos caracteres null, por ejemplo, "XYZ gráficos Editor\0Bald Eagle\0\0," donde \0 representa el valor null carácter. Si `lpszDescription` es **NULL**, no hay ninguna entrada correspondiente en el encabezado de metarchivo mejorado.  
  
 Aplicaciones utilizan el controlador de dominio creado por esta función para almacenar una imagen de gráficos en un metarchivo mejorado. El identificador identifica este controlador de dominio se puede pasar a cualquier función GDI.  
  
 Después de que una aplicación almacena una imagen en un metarchivo mejorado, puede mostrar la imagen en cualquier dispositivo de salida mediante una llamada a la `CDC::PlayMetaFile` (función). Cuando se muestra la imagen, Windows utiliza el rectángulo que señala el `lpBounds` parámetro y los datos de la resolución del dispositivo de referencia para colocar y escalar la imagen. El contexto de dispositivo devuelto por esta función contiene los mismos atributos predeterminados asociados a cualquier controlador de dominio nuevo.  
  
 Las aplicaciones deben utilizar Win32 **GetWinMetaFileBits** función para convertir un metarchivo mejorado en el formato de metarchivo de Windows anterior.  
  
 Debe usar el nombre de archivo para el metarchivo mejorado el. Extensión EMF.  
  
## <a name="see-also"></a>Vea también  
 [CDC (clase)](../../mfc/reference/cdc-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)



