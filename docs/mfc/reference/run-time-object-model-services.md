---
title: Servicios del modelo de objeto de tiempo de ejecución | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- run-time object model services macros
ms.assetid: 4a3e79df-2ee3-43a4-8193-20298828de85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 138275468801f3db2f2c64f06e5a505c412723b5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050962"
---
# <a name="run-time-object-model-services"></a>Servicios del modelo de objetos en tiempo de ejecución
Las clases [CObject](../../mfc/reference/cobject-class.md) y [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) encapsular varios servicios de objeto, incluido el acceso a información de clases en tiempo de ejecución, la serialización y la creación de objetos dinámicos. Todas las clases derivadas de `CObject` heredan esta funcionalidad.  
  
 Acceso a la información de clase en tiempo de ejecución le permite determinar la información acerca de la clase de un objeto en tiempo de ejecución. La capacidad para determinar la clase de un objeto en tiempo de ejecución es útil cuando necesita adicional comprobación de tipos de argumentos de función y cuándo se debe escribir código especial basado en la clase de un objeto. Información de clases en tiempo de ejecución no se admite directamente en el lenguaje C++.  
  
 La serialización es el proceso de escritura o lectura del contenido de un objeto a o desde un archivo. Puede utilizar la serialización para almacenar contenido de un objeto, incluso después de salir de la aplicación. El objeto, a continuación, se puede leer desde el archivo cuando se reinicia la aplicación. Estos objetos de datos se consideran "persistente".  
  
 Creación de objetos dinámicos le permite crear un objeto de una clase especificada en tiempo de ejecución. Por ejemplo, document, vista y objetos de fotogramas deben admitir la creación dinámica porque el marco debe crear de forma dinámica.  
  
 En la tabla siguiente se enumera las macros MFC que admiten la creación dinámica, la serialización y la información de clases en tiempo de ejecución.  
  
 Para obtener más información sobre estos servicios de objeto de tiempo de ejecución y la serialización, vea el artículo [CObject (clase): acceso a información de clase de tiempo de ejecución](../../mfc/accessing-run-time-class-information.md).  
  
### <a name="run-time-object-model-services-macros"></a>Macros de servicios del modelo de objetos de tiempo de ejecución  
  


|||  
|-|-|  
|[DECLARE_DYNAMIC](#declare_dynamic)|Permite el acceso a la información de clase en tiempo de ejecución (debe usarse en la declaración de clase).|  
|[DECLARE_DYNCREATE](#declare_dyncreate)|Permite el acceso a la información de clase en tiempo de ejecución (debe usarse en la declaración de clase) y la creación dinámica.|  
|[DECLARE_SERIAL](#declare_serial)|Permite el acceso a la información de clase en tiempo de ejecución (debe usarse en la declaración de clase) y serialización.|  
|[IMPLEMENT_DYNAMIC](#implement_dynamic)|Permite el acceso a la información de clase en tiempo de ejecución (debe usarse en la implementación de la clase).|  
|[IMPLEMENT_DYNCREATE](#implement_dyncreate)|Permite el acceso a la información de tiempo de ejecución (debe usarse en la implementación de la clase) y la creación dinámica.|  
|[IMPLEMENT_SERIAL](#implement_serial)|Permite la serialización y el acceso a la información de clase en tiempo de ejecución (debe usarse en la implementación de la clase).|  
|[RUNTIME_CLASS](#runtime_class)|Devuelve el `CRuntimeClass` estructura que corresponde a la clase con nombre.|  


 OLE con frecuencia requiere la creación dinámica de objetos en tiempo de ejecución. Por ejemplo, una aplicación de servidor OLE debe ser capaz de crear elementos OLE dinámicamente en respuesta a una solicitud de un cliente. De forma similar, un servidor de automatización debe ser capaz de crear elementos en respuesta a las solicitudes de los clientes de automatización.  
  
 La biblioteca Microsoft Foundation Class proporciona dos macros específicas a OLE.  
  
### <a name="dynamic-creation-of-ole-objects"></a>Creación dinámica de objetos OLE  

 






|||  
|-|-|  
|[AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)|Determina si la biblioteca de controles comunes implementa la API especificada.|
|[AFX_COMCTL32_IF_EXISTS2](#afx_comctl32_if_exists2)|Determina si la biblioteca de controles comunes implementa la API especificada.|
|[DECLARE_OLECREATE](#declare_olecreate)|Permite a los objetos que se crearán mediante la automatización OLE.|  
|[DECLARE_OLECTLTYPE](#declare_olectltype)|Declara el `GetUserTypeNameID` y `GetMiscStatus` las funciones miembro de la clase del control.|
|[DECLARE_PROPPAGEIDS](#declare_proppageids)|Declara que el control OLE proporciona una lista de páginas de propiedades para mostrar sus propiedades.|
|[IMPLEMENT_OLECREATE](#implement_olecreate)|Permite a los objetos que va a crear el sistema OLE.|  
|[IMPLEMENT_OLECTLTYPE](#implement_olectltype)|Implementa el `GetUserTypeNameID` y `GetMiscStatus` las funciones miembro de la clase del control.|  
|[IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags)|Ya sea esta macro o [IMPLEMENT_OLECREATE](#implement_olecreate) debe aparecer en el archivo de implementación para cualquier clase que utiliza `DECLARE_OLECREATE`. |

## <a name="afx_comctl32_if_exists"></a> AFX_COMCTL32_IF_EXISTS
Determina si la biblioteca de controles comunes implementa la API especificada.  
   
### <a name="syntax"></a>Sintaxis  
  ```  
AFX_COMCTL32_IF_EXISTS(  proc );  
```
### <a name="parameters"></a>Parámetros  
 *proc*  
 Puntero a una cadena terminada en null que contiene el nombre de función, o especifica el valor ordinal de la función. Si este parámetro es un valor ordinal, debe estar en la palabra de orden inferior; la palabra de orden superior debe ser cero. Este parámetro debe estar en formato Unicode.  
   
### <a name="remarks"></a>Comentarios  
 Use esta macro para determinar si la biblioteca de controles comunes la función especificada por *proc* (en lugar de llamar [GetProcAddress](https://msdn.microsoft.com/library/windows/desktop/ms683212).  
   
### <a name="requirements"></a>Requisitos  
 afxcomctl32.h, afxcomctl32.inl  
   
### <a name="see-also"></a>Vea también  
 [Biblioteca de controles de aislamiento de los comunes MFC](../isolation-of-the-mfc-common-controls-library.md) [AFX_COMCTL32_IF_EXISTS2](#afx_comctl32_if_exists2)
 
## <a name="afx_comctl32_if_exists2"></a>  AFX_COMCTL32_IF_EXISTS2
Determina si la biblioteca de controles comunes implementa la API especificada (se trata de la versión Unicode de [AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)).  
   
### <a name="syntax"></a>Sintaxis    
```  
AFX_COMCTL32_IF_EXISTS2( proc );  
```
### <a name="parameters"></a>Parámetros  
 *proc*  
 Puntero a una cadena terminada en null que contiene el nombre de función, o especifica el valor ordinal de la función. Si este parámetro es un valor ordinal, debe estar en la palabra de orden inferior; la palabra de orden superior debe ser cero. Este parámetro debe estar en formato Unicode.  
   
### <a name="remarks"></a>Comentarios  
 Use esta macro para determinar si la biblioteca de controles comunes la función especificada por *proc* (en lugar de llamar [GetProcAddress](https://msdn.microsoft.com/library/windows/desktop/ms683212). Esta macro es la versión Unicode de AFX_COMCTL32_IF_EXISTS.  
   
### <a name="requirements"></a>Requisitos  
 afxcomctl32.h, afxcomctl32.inl  
   
### <a name="see-also"></a>Vea también  
 [Biblioteca de controles de aislamiento de los comunes MFC](../isolation-of-the-mfc-common-controls-library.md) [AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)



##  <a name="declare_dynamic"></a>  DECLARE_DYNAMIC  
 Agrega la capacidad para tener acceso a información de tiempo de ejecución acerca de la clase de un objeto al derivar una clase de `CObject`.  
  
```
DECLARE_DYNAMIC(class_name) 
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre real de la clase.  
  
### <a name="remarks"></a>Comentarios  
 Agregue la macro DECLARE_DYNAMIC al módulo de encabezado (. h) para la clase y luego incluya ese módulo en todos los módulos de .cpp que necesitan tener acceso a objetos de esta clase.  
  
 Si utiliza las macros DECLARE_ dinámica y IMPLEMENT_DYNAMIC tal como se describe, a continuación, puede usar la macro RUNTIME_CLASS y `CObject::IsKindOf` función para determinar la clase de los objetos en tiempo de ejecución.  
  
 Si DECLARE_DYNAMIC se incluye en la declaración de clase, IMPLEMENT_DYNAMIC deben incluirse en la implementación de la clase.  
  
 Para obtener más información sobre la macro DECLARE_DYNAMIC, consulte [temas de la clase de CObject](../../mfc/using-cobject.md).  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [IMPLEMENT_DYNAMIC](#implement_dynamic).  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="declare_dyncreate"></a>  DECLARE_DYNCREATE  
 Permite a los objetos de `CObject`-las clases derivadas para crearse dinámicamente en tiempo de ejecución.  
  
```
DECLARE_DYNCREATE(class_name)   
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre real de la clase.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo utiliza esta capacidad para crear nuevos objetos de forma dinámica. Por ejemplo, la nueva vista creada cuando se abre un nuevo documento. Documento, vista y las clases de marco deben admitir la creación dinámica porque el marco debe crear de forma dinámica.  
  
 Agregar la macro DECLARE_DYNCREATE en el módulo .h para la clase y luego incluya ese módulo en todos los módulos de .cpp que necesitan tener acceso a objetos de esta clase.  
  
 Si DECLARE_DYNCREATE se incluye en la declaración de clase, IMPLEMENT_DYNCREATE deben incluirse en la implementación de la clase.  
  
 Para obtener más información sobre la macro DECLARE_DYNCREATE, consulte [temas de la clase de CObject](../../mfc/using-cobject.md).  
  
> [!NOTE]
>  La macro DECLARE_DYNCREATE incluye toda la funcionalidad de DECLARE_DYNAMIC.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [IMPLEMENT_DYNCREATE](#implement_dyncreate).  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

 
## <a name="declareolectltype"></a>DECLARE_OLECTLTYPE
Declara el `GetUserTypeNameID` y `GetMiscStatus` las funciones miembro de la clase del control.  
   
### <a name="syntax"></a>Sintaxis    
```
DECLARE_OLECTLTYPE( class_name )  
```
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre de la clase de control.  
   
### <a name="remarks"></a>Comentarios  
 `GetUserTypeNameID` y `GetMiscStatus` son funciones virtuales puras, declaradas en `COleControl`. Dado que estas funciones son puras virtual, se debe invalidar en la clase del control. Además de DECLARE_OLECTLTYPE, debe agregar el implement_olectltype (macro) a la declaración de clase del control.  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxctl.h  
   
### <a name="see-also"></a>Vea también  
 [IMPLEMENT_OLECTLTYPE](#implement_olectltype)
 

## <a name="declareproppageids"></a>DECLARE_PROPPAGEIDS
Declara que el control OLE proporciona una lista de páginas de propiedades para mostrar sus propiedades.  
   
### <a name="syntax"></a>Sintaxis    
```
DECLARE_PROPPAGEIDS( class_name )  
```
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre de la clase de control que posee las páginas de propiedades.  
   
### <a name="remarks"></a>Comentarios  
 Use el `DECLARE_PROPPAGEIDS` macro al final de la declaración de clase. A continuación, en el archivo .cpp que define las funciones miembro de la clase, use la `BEGIN_PROPPAGEIDS` (macro), las entradas de macro para cada una de las páginas de propiedades del control y el `END_PROPPAGEIDS` macro para declarar el final de la lista de la página de propiedades.  
  
 Para obtener más información sobre las páginas de propiedades, vea el artículo [controles ActiveX: páginas de propiedades](../mfc-activex-controls-property-pages.md).  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxctl.h  
   
### <a name="see-also"></a>Vea también   
 [BEGIN_PROPPAGEIDS](#begin_proppageids)   
 [END_PROPPAGEIDS](#end_proppageids)

##  <a name="declare_serial"></a>  DECLARE_SERIAL  
 Genera el código del encabezado de C++ necesario para un `CObject`-clase derivada que se puede serializar.  
  
```
DECLARE_SERIAL(class_name)   
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre real de la clase.  
  
### <a name="remarks"></a>Comentarios  
 La serialización es el proceso de escribir o leer el contenido de un objeto a y desde un archivo.  
  
 Utilice la macro DECLARE_SERIAL en un módulo. h y, a continuación, incluir ese módulo en todos los módulos de .cpp que necesitan tener acceso a objetos de esta clase.  
  
 Si DECLARE_SERIAL se incluye en la declaración de clase, IMPLEMENT_SERIAL deben incluirse en la implementación de la clase.  
  
 La macro DECLARE_SERIAL incluye toda la funcionalidad de DECLARE_DYNAMIC y DECLARE_DYNCREATE.  
  
 Puede usar la macro AFX_API para exportar automáticamente la `CArchive` operador de extracción para las clases que use las macros DECLARE_SERIAL y IMPLEMENT_SERIAL. Corchete angular de cierre las declaraciones de clase (que se encuentra en el archivo. h) con el código siguiente:  
  
 [!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]  
  
 Para obtener más información sobre la macro DECLARE_SERIAL, consulte [temas de la clase de CObject](../../mfc/using-cobject.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCObjectSample#21](../../mfc/codesnippet/cpp/run-time-object-model-services_2.h)]  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="implement_dynamic"></a>  IMPLEMENT_DYNAMIC  
 Genera el código de C++ necesario para una dinámica `CObject`-derivados de clase con acceso de tiempo de ejecución para el nombre de clase y la posición dentro de la jerarquía.  
  
```
IMPLEMENT_DYNAMIC(class_name, base_class_name)  
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre real de la clase.  
  
*BASE_CLASS_NAME*<br/>
El nombre de la clase base.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la macro IMPLEMENT_DYNAMIC en un módulo .cpp y, a continuación, vincule el código objeto resultante solo una vez.  
  
 Para obtener más información, consulte [temas de la clase de CObject](../../mfc/using-cobject.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCObjectSample#2](../../mfc/codesnippet/cpp/run-time-object-model-services_3.h)]  
  
 [!code-cpp[NVC_MFCCObjectSample#3](../../mfc/codesnippet/cpp/run-time-object-model-services_4.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="implement_dyncreate"></a>  IMPLEMENT_DYNCREATE  
 Permite a los objetos de `CObject`-las clases derivadas para que se crean dinámicamente en ejecución cuando se usa con la macro DECLARE_DYNCREATE de tiempo.  
  
```
IMPLEMENT_DYNCREATE(class_name, base_class_name)   
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre real de la clase.  
  
 *BASE_CLASS_NAME*  
 El nombre real de la clase base.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo utiliza esta capacidad para la creación de nuevos objetos dinámicamente, por ejemplo, cuando lee un objeto desde el disco durante la serialización. Agregar la macro IMPLEMENT_DYNCREATE en el archivo de implementación de clase. Para obtener más información, consulte [temas de la clase de CObject](../../mfc/using-cobject.md).  
  
 Si utiliza las macros DECLARE_DYNCREATE e IMPLEMENT_DYNCREATE, a continuación, puede usar la macro RUNTIME_CLASS y `CObject::IsKindOf` función miembro para determinar la clase de los objetos en tiempo de ejecución.  
  
 Si DECLARE_DYNCREATE se incluye en la declaración de clase, IMPLEMENT_DYNCREATE deben incluirse en la implementación de la clase.  
  
 Tenga en cuenta que esta definición de macro invocará el constructor predeterminado para la clase. Si la clase se implementa explícitamente un constructor no trivial, explícitamente debe implementar también el constructor predeterminado. El constructor predeterminado que se puede agregar a la clase **privada** o **protegido** secciones de miembro para impedir que se llama desde fuera de la implementación de la clase.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCObjectSample#22](../../mfc/codesnippet/cpp/run-time-object-model-services_5.h)]  
  
 [!code-cpp[NVC_MFCCObjectSample#23](../../mfc/codesnippet/cpp/run-time-object-model-services_6.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

## <a name="implement_olecreate_flags"></a>  IMPLEMENT_OLECREATE_FLAGS
Ya sea esta macro o [IMPLEMENT_OLECREATE](#implement_olecreate) debe aparecer en el archivo de implementación para cualquier clase que utiliza DECLARE_OLECREATE.  
   
### <a name="syntax"></a>Sintaxis    
```
IMPLEMENT_OLECREATE_FLAGS( class_name, external_name, nFlags, 
    l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)  
  
```
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre real de la clase.  
  
 *external_name*  
 El nombre de objeto que se expone a otras aplicaciones (entrecomilladas comillas).  
  
 *nFlags*  
 Contiene uno o varios de los siguientes indicadores:  
  
    -   `afxRegInsertable` Permite el control aparezca en el cuadro de diálogo Insertar objeto para los objetos OLE.    
    -   `afxRegApartmentThreading` Establece el modelo de subprocesos en el registro para ThreadingModel = apartamento.    
    -   `afxRegFreeThreading` Establece el modelo de subprocesos en el registro para ThreadingModel = gratis.  
      
         Puede combinar las dos marcas `afxRegApartmentThreading` y `afxRegFreeThreading` establecer ThreadingModel = Both. Consulte [InprocServer32](/windows/desktop/com/inprocserver32) en el SDK de Windows para obtener más información sobre el registro del modelo de subprocesos. 
   
 *l*, *w1*, *w2*, *b1*, *b2*, *b3*, *b4* , *b5*, *b6*, *b7*, *b8*  
 Componentes de CLSID de la clase.  
   
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Si usa IMPLEMENT_OLECREATE_FLAGS, puede especificar qué modelo de subprocesos es compatible con el objeto utilizando el *nFlags* parámetro. Si desea admitir solo el modelo simple-Threading, utilice IMPLEMENT_OLECREATE.  
  
 External name es el identificador que se expone a otras aplicaciones. Las aplicaciones cliente utilizar el nombre externo para solicitar un objeto de esta clase desde un servidor de automatización.  
  
 El identificador de clase OLE es un identificador único de 128 bits para el objeto. Está formado por uno **largo**, dos **WORD**s y ocho **bytes**s, tal como está representada por *l*, *w1*, *w2*, y *b1* a través de *b8* en la descripción de sintaxis. Los asistentes de código y el Asistente para aplicaciones creación Id. de clase OLE único para usted según sea necesario.  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdisp.h  
   
### <a name="see-also"></a>Vea también  
 [Macros y funciones globales](mfc-macros-and-globals.md)   
 [DECLARE_OLECREATE](#declare_olecreate)   
 [Clave CLSID](/windows/desktop/com/clsid-key-hklm)


## <a name="implement_olecreate"></a> IMPLEMENT_OLECTLTYPE
Implementa el `GetUserTypeNameID` y `GetMiscStatus` las funciones miembro de la clase del control.  
   
### <a name="syntax"></a>Sintaxis    
```
DECLARE_OLECTLTYPE( class_name, idsUserTypeName, dwOleMisc )  
```
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre de la clase de control.  
  
 *idsUserTypeName*  
 El identificador de recurso de cadena que contiene el nombre externo del control.  
  
 *dwOleMisc*  
 Una enumeración que contiene uno o más marcadores. Para obtener más información acerca de esta enumeración, vea [OLEMISC](/windows/desktop/api/oleidl/ne-oleidl-tagolemisc) en el SDK de Windows.  
   
### <a name="remarks"></a>Comentarios  
 Además de IMPLEMENT_OLECTLTYPE, debe agregar el declare_olectltype (macro) a la declaración de clase del control.  
  
 El `GetUserTypeNameID` función miembro devuelve la cadena de recurso que identifica la clase del control. `GetMiscStatus` Devuelve los bits OLEMISC para el control. Esta enumeración especifica una colección de valores que describen varias características del control. Para obtener una descripción completa de la configuración de OLEMISC, consulte [OLEMISC](/windows/desktop/api/oleidl/ne-oleidl-tagolemisc) en el SDK de Windows.  
  
> [!NOTE]
>  La configuración predeterminada utilizada por el ActiveX ControlWizard es: OLEMISC_ACTIVATEWHENVISIBLE, OLEMISC_SETCLIENTSITEFIRST, OLEMISC_INSIDEOUT, OLEMISC_CANTLINKINSIDE y OLEMISC_RECOMPOSEONRESIZE.  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxctl.h  
   
### <a name="see-also"></a>Vea también  
 [Macros y funciones globales](mfc-macros-and-globals.md)   
 [DECLARE_OLECTLTYPE](#declare_olectltype)

##  <a name="implement_serial"></a>  IMPLEMENT_SERIAL  
 Genera el código de C++ necesario para una dinámica `CObject`-derivados de clase con acceso de tiempo de ejecución para el nombre de clase y la posición dentro de la jerarquía.  
  
```
IMPLEMENT_SERIAL(class_name, base_class_name, wSchema)  
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre real de la clase.  
  
 *BASE_CLASS_NAME*  
 El nombre de la clase base.  
  
 *wSchema*  
 Un UINT "número de versión" que se va a codificar en el archivo para habilitar un programa de deserialización identificar y controlar los datos creados por versiones anteriores del programa versiones. El número de esquema de clase no debe ser -1.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la macro IMPLEMENT_SERIAL en un módulo de cpp. a continuación, vincule el código objeto resultante solo una vez.  
  
 Puede usar la macro AFX_API para exportar automáticamente la `CArchive` operador de extracción para las clases que use las macros DECLARE_SERIAL y IMPLEMENT_SERIAL. Corchete angular de cierre las declaraciones de clase (que se encuentra en el archivo. h) con el código siguiente:  
  
 [!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]  
  
 Para obtener más información, consulte el [temas de la clase de CObject](../../mfc/using-cobject.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCObjectSample#24](../../mfc/codesnippet/cpp/run-time-object-model-services_7.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="runtime_class"></a>  RUNTIME_CLASS  
 Obtiene la estructura de clases de tiempo de ejecución desde el nombre de una clase de C++.  
  
```
RUNTIME_CLASS(class_name)  
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre real de la clase (no está entrecomillada comillas).  
  
### <a name="remarks"></a>Comentarios  
 RUNTIME_CLASS devuelve un puntero a un [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) estructura de la clase especificada por *class_name*. Solo `CObject`-las clases derivadas declaradas con DECLARE_DYNAMIC, DECLARE_DYNCREATE o DECLARE_SERIAL devolverá punteros a un `CRuntimeClass` estructura.  
  
 Para obtener más información, consulte [temas de la clase de CObject](../../mfc/using-cobject.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCObjectSample#25](../../mfc/codesnippet/cpp/run-time-object-model-services_8.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 
   
##  <a name="declare_olecreate"></a>  DECLARE_OLECREATE  
 Permite a los objetos de `CCmdTarget`-las clases derivadas para crearse mediante la automatización OLE.  
  
```
DECLARE_OLECREATE(class_name) 
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre real de la clase.  
  
### <a name="remarks"></a>Comentarios  
 Esta macro permite que otras aplicaciones habilitadas para OLE crear objetos de este tipo.  
  
 Agregue el declare_olecreate (macro) en el módulo .h para la clase y, a continuación, incluir ese módulo en todos los módulos de .cpp que necesitan tener acceso a objetos de esta clase.  
  
 Si DECLARE_OLECREATE se incluye en la declaración de clase, IMPLEMENT_OLECREATE deben incluirse en la implementación de la clase. También debe usar una declaración de clase mediante DECLARE_OLECREATE DECLARE_DYNCREATE o DECLARE_SERIAL.  

### <a name="requirements"></a>Requisitos  
 **Encabezado**: afxdisp.h  

##  <a name="implement_olecreate"></a>  IMPLEMENT_OLECREATE  
 Ya sea esta macro o [IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags) debe aparecer en el archivo de implementación para cualquier clase que utiliza `DECLARE_OLECREATE`.  
  
```
IMPLEMENT_OLECREATE(class_name, external_name, l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)  
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre real de la clase.  
  
 *external_name*  
 El nombre de objeto que se expone a otras aplicaciones (entrecomilladas comillas).  
  
 *l*, *w1*, *w2*, *b1*, *b2*, *b3*, *b4* , *b5*, *b6*, *b7*, *b8*  
 Componentes de CLSID de la clase.  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Si usas IMPLEMENT_OLECREATE, de forma predeterminada, admite solo el modelo de subprocesamiento único. Si usa IMPLEMENT_OLECREATE_FLAGS, puede especificar qué modelo de subprocesos es compatible con el objeto utilizando el *nFlags* parámetro.  
  
 External name es el identificador que se expone a otras aplicaciones. Las aplicaciones cliente utilizar el nombre externo para solicitar un objeto de esta clase desde un servidor de automatización.  
  
 El identificador de clase OLE es un identificador único de 128 bits para el objeto. Está formado por uno **largo**, dos **WORD**s y ocho **bytes**s, tal como está representada por *l*, *w1*, *w2*, y *b1* a través de *b8* en la descripción de sintaxis. Los asistentes de código y el Asistente para aplicaciones creación Id. de clase OLE único para usted según sea necesario.  

### <a name="requirements"></a>Requisitos  
 **Encabezado**: afxdisp.h 

## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)

