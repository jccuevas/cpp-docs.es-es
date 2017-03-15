---
title: CMetaFileDC (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMetaFileDC
dev_langs:
- C++
helpviewer_keywords:
- CMetaFileDC class
- Windows metafiles [C++]
- metafiles, implementing
ms.assetid: ffce60fa-4181-4d46-9832-25e46fad4db4
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 4bff4d7601c4ffbc6fe5cbe73f5e057b79abf1e5
ms.lasthandoff: 02/24/2017

---
# <a name="cmetafiledc-class"></a>CMetaFileDC (clase)
Implementa un metarchivo de Windows, que contiene una secuencia de comandos de la interfaz de dispositivo gráfico (GDI) que puede volver a consultar para crear la imagen o el texto que desee.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMetaFileDC : public CDC  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMetaFileDC::CMetaFileDC](#cmetafiledc)|Construye un objeto `CMetaFileDC`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMetaFileDC::Close](#close)|Cierra el contexto de dispositivo y crea un identificador de metarchivo.|  
|[CMetaFileDC::CloseEnhanced](#closeenhanced)|Cierra un contexto de dispositivo de metarchivo mejorado y crea un identificador de metarchivo mejorado.|  
|[CMetaFileDC::Create](#create)|Crea el contexto de dispositivo de metarchivo de Windows y lo adjunta a la `CMetaFileDC` objeto.|  
|[CMetaFileDC::CreateEnhanced](#createenhanced)|Crea un contexto de dispositivo de metarchivo para un metarchivo de formato mejorado.|  
  
## <a name="remarks"></a>Comentarios  
 Para implementar un metarchivo de Windows, cree primero un `CMetaFileDC` objeto. Invocar el `CMetaFileDC` constructor, a continuación, llame a la [crear](#create) función miembro, que crea un contexto de dispositivo de metarchivo de Windows y lo adjunta a la `CMetaFileDC` objeto.  
  
 Enviar a continuación la `CMetaFileDC` objeto de la secuencia de `CDC` comandos GDI que piensa para poder reproducir. Únicamente los comandos GDI que creación una salida, como `MoveTo` y `LineTo`, se puede utilizar.  
  
 Después de enviar los comandos que desee en el metarchivo, llame a la **cerrar** función miembro, que cierra los contextos de dispositivo de metarchivo y devuelve un identificador de metarchivo. A continuación, eliminarlos de la `CMetaFileDC` objeto.  
  
 [CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile) , a continuación, puede utilizar el identificador del metarchivo para reproducir el metarchivo repetidamente. Metarchivo también puede ser manipulado por las funciones de Windows como [CopyMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183480), que copia un metarchivo en disco.  
  
 Cuando ya no es necesario el metarchivo, eliminarla de la memoria con el [DeleteMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183537) función de Windows.  
  
 También puede implementar la `CMetaFileDC` objeto por lo que puede controlar las llamadas de salida y atributo GDI llama como `GetTextExtent`. Un metarchivo de este tipo es más flexible y pueden más fácil reutilizar código GDI general, que a menudo, consta de una combinación de las llamadas de salida y el atributo. El `CMetaFileDC` clase hereda dos contextos de dispositivo, `m_hDC` y `m_hAttribDC`, de `CDC`. El `m_hDC` contexto de dispositivo administra todo [CDC](../../mfc/reference/cdc-class.md) llamadas de salida de la GDI y el `m_hAttribDC` contexto de dispositivo administra todo `CDC` GDI atributo llama. Normalmente, estos contextos de dos dispositivo hacen referencia al mismo dispositivo. En el caso de `CMetaFileDC`, el controlador de dominio está establecido en **NULL** de forma predeterminada.  
  
 Crear un segundo contexto de dispositivo que apunta a la pantalla, impresora o dispositivo que no sea un metarchivo, a continuación, llame el `SetAttribDC` para asociar el nuevo contexto de dispositivo con la función miembro `m_hAttribDC`. Llamadas GDI para obtener información ahora se dirigirá a la nueva `m_hAttribDC`. Salida GDI llama irá a `m_hDC`, que representa el metarchivo.  
  
 Para obtener más información sobre `CMetaFileDC`, consulte [contextos de dispositivo](../../mfc/device-contexts.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CMetaFileDC`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxext.h  
  
##  <a name="a-nameclosea--cmetafiledcclose"></a><a name="close"></a>CMetaFileDC::Close  
 Cierra el contexto de dispositivo de metarchivo y crea un identificador de metarchivo de Windows que puede usar para reproducir el metarchivo mediante la [CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile) función miembro.  
  
```  
HMETAFILE Close();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Válido **HMETAFILE** si la función se realiza correctamente; en caso contrario **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 El identificador del metarchivo de Windows también puede utilizarse para manipular el metarchivo con funciones de Windows como [CopyMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183480).  
  
 Eliminar el metarchivo tras su uso mediante una llamada a Windows [DeleteMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183537) (función).  
  
##  <a name="a-namecloseenhanceda--cmetafiledccloseenhanced"></a><a name="closeenhanced"></a>CMetaFileDC::CloseEnhanced  
 Cierra un contexto de dispositivo de metarchivo mejorado y devuelve un identificador que identifica un metarchivo de formato mejorado.  
  
```  
HENHMETAFILE CloseEnhanced();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador de un metarchivo mejorado, si es correcto; de lo contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Una aplicación puede utilizar el identificador de metarchivo mejorado devuelto por esta función para realizar las siguientes tareas:  
  
-   Mostrar una imagen almacenada en un metarchivo mejorado  
  
-   Crear copias del metarchivo mejorado  
  
-   Enumerar, editar o copiar registros individuales del metarchivo mejorado  
  
-   Recuperar una descripción opcional del contenido del metarchivo desde el encabezado del metarchivo mejorado  
  
-   Recuperar una copia del encabezado del metarchivo mejorado  
  
-   Recuperar una copia binaria del metarchivo mejorado  
  
-   Enumerar los colores de la paleta opcional  
  
-   Convertir un metarchivo de formato mejorado en un metarchivo de formato de Windows  
  
 Cuando la aplicación ya no necesita el identificador del metarchivo mejorado, debe liberar el identificador mediante una llamada a Win32 **DeleteEnhMetaFile** (función).  
  
##  <a name="a-namecmetafiledca--cmetafiledccmetafiledc"></a><a name="cmetafiledc"></a>CMetaFileDC::CMetaFileDC  
 Construir un `CMetaFileDC` objeto en dos pasos.  
  
```  
CMetaFileDC();
```  
  
### <a name="remarks"></a>Comentarios  
 En primer lugar, llame a `CMetaFileDC`, a continuación, llame a **crear**, que crea el contexto de dispositivo de metarchivo de Windows y lo adjunta a la `CMetaFileDC` objeto.  
  
##  <a name="a-namecreatea--cmetafiledccreate"></a><a name="create"></a>CMetaFileDC::Create  
 Construir un `CMetaFileDC` objeto en dos pasos.  
  
```  
BOOL Create(LPCTSTR lpszFilename = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszFilename*  
 Apunta a una cadena de caracteres terminada en null. Especifica el nombre de archivo del metarchivo que se va a crear. Si *lpszFilename* es **NULL**, se crea un nuevo metarchivo en la memoria.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 En primer lugar, llame al constructor de `CMetaFileDC`, a continuación, llame a **crear**, que crea el contexto de dispositivo de metarchivo de Windows y lo adjunta a la `CMetaFileDC` objeto.  
  
##  <a name="a-namecreateenhanceda--cmetafiledccreateenhanced"></a><a name="createenhanced"></a>CMetaFileDC::CreateEnhanced  
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
 Identifica un dispositivo de referencia de metarchivo mejorado.  
  
 `lpszFileName`  
 Apunta a una cadena de caracteres terminada en null. Especifica el nombre de archivo de metarchivo mejorado a crearse. Si este parámetro es **NULL**, metarchivo mejorado está basada en memoria y su contenido que se pierden cuando se destruye el objeto o cuando Win32 **DeleteEnhMetaFile** se llama la función.  
  
 `lpBounds`  
 Apunta a un [RECT](../../mfc/reference/rect-structure1.md) estructura de datos o un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que especifica las dimensiones en **HIMETRIC** unidades (en incrementos de.01 milímetros) de la imagen que se almacenará en el metarchivo mejorado.  
  
 `lpszDescription`  
 Apunta a una cadena terminada en cero que especifica el nombre de la aplicación que creó la imagen, así como el título de la imagen.  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador del contexto de dispositivo de metarchivo mejorado, si es correcto; de lo contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Este controlador de dominio puede utilizarse para almacenar una imagen independiente del dispositivo.  
  
 Windows usa el dispositivo de referencia identificado por el `pDCRef` parámetro para registrar la resolución y las unidades del dispositivo en el que apareció originalmente una imagen. Si el `pDCRef` parámetro es **NULL**, que utiliza el dispositivo de presentación actual como referencia.  
  
 Los miembros izquierdos y superiores de la `RECT` estructura de datos que señala el `lpBounds` parámetro debe ser inferior a los miembros de la derecha y abajo, respectivamente. Puntos a lo largo de los bordes del rectángulo se incluyen en la imagen. Si `lpBounds` es **NULL**, la interfaz de dispositivo gráfico (GDI) calcula las dimensiones del rectángulo más pequeño que puede encerrar la imagen dibujada por la aplicación. El `lpBounds` parámetro debe especificarse siempre que sea posible.  
  
 La cadena señalada por el `lpszDescription` parámetro debe contener un carácter null entre el nombre de la aplicación y el nombre de imagen y debe terminar con dos caracteres null, por ejemplo, "XYZ gráficos Editor\0Bald Eagle\0\0," donde \0 representa el carácter nulo. Si `lpszDescription` es **NULL**, no hay ninguna entrada correspondiente en el encabezado del metarchivo mejorado.  
  
 Aplicaciones utilizan el controlador de dominio creado por esta función para almacenar una imagen de gráficos en un metarchivo mejorado. El identificador que identifica este controlador de dominio se puede pasar a cualquier función GDI.  
  
 Después de que una aplicación almacena una imagen en un metarchivo mejorado, puede mostrar la imagen en cualquier dispositivo de salida llamando el `CDC::PlayMetaFile` (función). Cuando se muestra la imagen, Windows utiliza el rectángulo que apunta el `lpBounds` parámetro y los datos de la resolución del dispositivo de referencia de posición y escalar la imagen. El contexto de dispositivo devuelto por esta función contiene los mismos atributos predeterminados asociados a cualquier controlador de dominio.  
  
 Las aplicaciones deben utilizar Win32 **GetWinMetaFileBits** función para convertir un metarchivo mejorado con el formato de metarchivo de Windows anterior.  
  
 Debe utilizar el nombre de archivo para el metarchivo mejorado el. Extensión EMF.  
  
## <a name="see-also"></a>Vea también  
 [CDC (clase)](../../mfc/reference/cdc-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)




