---
title: "Servicios de modelo de objetos en tiempo de ejecución | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- run-time object model services macros
ms.assetid: 4a3e79df-2ee3-43a4-8193-20298828de85
caps.latest.revision: 15
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
ms.sourcegitcommit: b943ef8dd652df061965fe81ecc9c08115636141
ms.openlocfilehash: c11d9a2d56f17d814873d36868b8fb6cf3deac43
ms.lasthandoff: 04/04/2017

---
# <a name="run-time-object-model-services"></a>Servicios del modelo de objetos en tiempo de ejecución
Las clases de [CObject](../../mfc/reference/cobject-class.md) y [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) encapsular varios servicios de objeto, incluido el acceso a información de clase en tiempo de ejecución, la serialización y la creación dinámica de objetos. Todas las clases derivadas de `CObject` heredan esta funcionalidad.  
  
 Acceso a la información de clase en tiempo de ejecución permite determinar la información acerca de la clase de un objeto en tiempo de ejecución. La capacidad para determinar la clase de un objeto en tiempo de ejecución es útil cuando es necesario adicional-comprobación de tipos de argumentos de función y cuándo se debe escribir código especial basado en la clase de un objeto. Información de clase en tiempo de ejecución no se admite directamente en el lenguaje C++.  
  
 La serialización es el proceso de escritura o lectura del contenido de un objeto a o desde un archivo. Puede utilizar la serialización para almacenar el contenido de un objeto incluso después de que salga de la aplicación. A continuación, se puede leer el objeto desde el archivo cuando se reinicie la aplicación. Se dice que estos objetos de datos "persistentes."  
  
 Creación de objetos dinámicos le permite crear un objeto de una clase especificada en tiempo de ejecución. Por ejemplo, documento, vista y objetos de marco deben admitir la creación dinámica porque el marco de trabajo necesita crear de forma dinámica.  
  
 En la tabla siguiente se enumera las macros MFC que admiten la creación dinámica, la serialización y la información de clase en tiempo de ejecución.  
  
 Para obtener más información sobre estos servicios de objeto de tiempo de ejecución y la serialización, vea el artículo [CObject (clase): obtener acceso a información de clase de tiempo de ejecución](../../mfc/accessing-run-time-class-information.md).  
  
### <a name="run-time-object-model-services-macros"></a>Macros de servicios del modelo de objetos de tiempo de ejecución  
  


|||  
|-|-|  
|[DECLARE_DYNAMIC](#declare_dynamic)|Permite el acceso a la información de clase en tiempo de ejecución (debe usarse en la declaración de clase).|  
|[DECLARE_DYNCREATE](#declare_dyncreate)|Permite la creación dinámica y acceso a la información de clase en tiempo de ejecución (debe usarse en la declaración de clase).|  
|[DECLARE_SERIAL](#declare_serial)|Permite el acceso a la información de clase en tiempo de ejecución (debe usarse en la declaración de clase) y serialización.|  
|[IMPLEMENT_DYNAMIC](#implement_dynamic)|Permite el acceso a la información de clase en tiempo de ejecución (debe usarse en la implementación de la clase).|  
|[IMPLEMENT_DYNCREATE](#implement_dyncreate)|Permite la creación dinámica y acceso a la información de tiempo de ejecución (debe usarse en la implementación de la clase).|  
|[IMPLEMENT_SERIAL](#implement_serial)|Permite la serialización y el acceso a la información de clase en tiempo de ejecución (debe usarse en la implementación de la clase).|  
|[RUNTIME_CLASS](#runtime_class)|Devuelve el `CRuntimeClass` estructura que corresponde a la clase con nombre.|  


 OLE normalmente requiere la creación dinámica de objetos en tiempo de ejecución. Por ejemplo, una aplicación de servidor OLE debe ser capaz de crear elementos OLE dinámicamente en respuesta a una solicitud de un cliente. De forma similar, un servidor de automatización debe ser capaz de crear elementos en respuesta a las solicitudes de los clientes de automatización.  
  
 La biblioteca Microsoft Foundation Class proporciona dos macros específicas a OLE.  
  
### <a name="dynamic-creation-of-ole-objects"></a>Creación dinámica de objetos OLE  

 






|||  
|-|-|  
|[AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)|Determina si la biblioteca de controles comunes implementa la API especificada.|
|[AFX_COMCTL32_IF_EXISTS2](#afx_comctl32_if_exists2)|Determina si la biblioteca de controles comunes implementa la API especificada.|
|[DECLARE_OLECREATE](#declare_olecreate)|Permite que los objetos que se crearán mediante automatización OLE.|  
|[DECLARE_OLECTLTYPE](#declare_olectltype)|Declara el **GetUserTypeNameID** y `GetMiscStatus` las funciones miembro de la clase del control.|
|[DECLARE_PROPPAGEIDS](#declare_proppageids)|Declara que el control OLE proporciona una lista de páginas de propiedades para mostrar sus propiedades.|
|[IMPLEMENT_OLECREATE](#implement_olecreate)|Permite que los objetos que se creará en el sistema OLE.|  
|[IMPLEMENT_OLECTLTYPE](#implement_olectltype)|Implementa el **GetUserTypeNameID** y `GetMiscStatus` las funciones miembro de la clase del control.|  
|[IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags)|Cualquier esta macro o [IMPLEMENT_OLECREATE](#implement_olecreate) deben aparecer en el archivo de implementación para cualquier clase que utiliza `DECLARE_OLECREATE`. |

## <a name="afx_comctl32_if_exists"></a>AFX_COMCTL32_IF_EXISTS
Determina si la biblioteca de controles comunes implementa la API especificada.  
   
### <a name="syntax"></a>Sintaxis  
  ```  
AFX_COMCTL32_IF_EXISTS(  proc );  
```
### <a name="parameters"></a>Parámetros  
 `proc`  
 Puntero a una cadena terminada en null que contiene el nombre de la función, o especifica el valor ordinal de la función. Si este parámetro es un valor ordinal, debe estar en la palabra de orden inferior; la palabra de orden superior debe ser cero. Este parámetro debe ser en Unicode.  
   
### <a name="remarks"></a>Comentarios  
 Utilice esta macro para determinar si la biblioteca de controles comunes de la función especificada por `proc` (en lugar de llamar [GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212).  
   
### <a name="requirements"></a>Requisitos  
 afxcomctl32.h, afxcomctl32.inl  
   
### <a name="see-also"></a>Vea también  
 [Biblioteca de controles de aislamiento de MFC Common](../isolation-of-the-mfc-common-controls-library.md)
 [AFX_COMCTL32_IF_EXISTS2](#afx_comctl32_if_exists2)
 
## <a name="afx_comctl32_if_exists2"></a>AFX_COMCTL32_IF_EXISTS2
Determina si la biblioteca de controles comunes implementa la API especificada (esta es la versión Unicode de [AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)).  
   
### <a name="syntax"></a>Sintaxis    
```  
AFX_COMCTL32_IF_EXISTS2( proc );  
```
### <a name="parameters"></a>Parámetros  
 `proc`  
 Puntero a una cadena terminada en null que contiene el nombre de la función, o especifica el valor ordinal de la función. Si este parámetro es un valor ordinal, debe estar en la palabra de orden inferior; la palabra de orden superior debe ser cero. Este parámetro debe ser en Unicode.  
   
### <a name="remarks"></a>Comentarios  
 Utilice esta macro para determinar si la biblioteca de controles comunes de la función especificada por `proc` (en lugar de llamar [GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212). Esta macro es la versión Unicode de `AFX_COMCTL32_IF_EXISTS`.  
   
### <a name="requirements"></a>Requisitos  
 afxcomctl32.h, afxcomctl32.inl  
   
### <a name="see-also"></a>Vea también  
 [Biblioteca de controles de aislamiento de MFC Common](../isolation-of-the-mfc-common-controls-library.md)
 [AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)



##  <a name="declare_dynamic"></a>DECLARE_DYNAMIC  
 Agrega la capacidad para tener acceso a información de tiempo de ejecución acerca de la clase de un objeto al derivar una clase de `CObject`.  
  
```
DECLARE_DYNAMIC(class_name) 
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre real de la clase.  
  
### <a name="remarks"></a>Comentarios  
 Agregar el `DECLARE_DYNAMIC` macro para el módulo de encabezado (. h) para la clase, a continuación, incluya ese módulo en todos los módulos de .cpp que necesitan tener acceso a objetos de esta clase.  
  
 Si usa el **DECLARE**_ **dinámica** y `IMPLEMENT_DYNAMIC` macros tal como se describe a continuación, puede usar el `RUNTIME_CLASS` macro y `CObject::IsKindOf` función para determinar la clase de los objetos en tiempo de ejecución.  
  
 Si `DECLARE_DYNAMIC` se incluye en la declaración de clase, a continuación, `IMPLEMENT_DYNAMIC` debe estar incluido en la implementación de la clase.  
  
 Para obtener más información sobre la `DECLARE_DYNAMIC` macro, consulte [temas de la clase de CObject](../../mfc/using-cobject.md).  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [IMPLEMENT_DYNAMIC](#implement_dynamic).  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="declare_dyncreate"></a>DECLARE_DYNCREATE  
 Permite a los objetos de `CObject`-las clases derivadas para crear dinámicamente en tiempo de ejecución.  
  
```
DECLARE_DYNCREATE(class_name)   
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre real de la clase.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo usa esta capacidad para crear nuevos objetos de forma dinámica. Por ejemplo, la nueva vista creada cuando se abre un nuevo documento. Documento, vista y las clases del marco deben admitir la creación dinámica porque el marco de trabajo necesita crear de forma dinámica.  
  
 Agregar el `DECLARE_DYNCREATE` macro en el módulo .h para la clase, a continuación, incluya ese módulo en todos los módulos de .cpp que necesitan tener acceso a objetos de esta clase.  
  
 Si `DECLARE_DYNCREATE` se incluye en la declaración de clase, a continuación, `IMPLEMENT_DYNCREATE` debe estar incluido en la implementación de la clase.  
  
 Para obtener más información sobre la `DECLARE_DYNCREATE` macro, consulte [temas de la clase de CObject](../../mfc/using-cobject.md).  
  
> [!NOTE]
>  El `DECLARE_DYNCREATE` macro incluye toda la funcionalidad de `DECLARE_DYNAMIC`.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [IMPLEMENT_DYNCREATE](#implement_dyncreate).  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

 
## <a name="declareolectltype"></a>DECLARE_OLECTLTYPE
Declara el **GetUserTypeNameID** y `GetMiscStatus` las funciones miembro de la clase del control.  
   
### <a name="syntax"></a>Sintaxis    
```
DECLARE_OLECTLTYPE( class_name )  
```
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre de la clase de control.  
   
### <a name="remarks"></a>Comentarios  
 **GetUserTypeNameID** y `GetMiscStatus` son funciones virtuales puras, declaradas en `COleControl`. Dado que estas funciones son puras virtual, se debe invalidar en la clase del control. Además **DECLARE_OLECTLTYPE**, debe agregar el `IMPLEMENT_OLECTLTYPE` macro a la declaración de clase de control.  
   
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
 Use la `DECLARE_PROPPAGEIDS` macro al final de la declaración de clase. A continuación, en el archivo .cpp que define las funciones de miembro para la clase, use la `BEGIN_PROPPAGEIDS` (macro), las entradas de macro para cada una de las páginas de propiedades del control y el `END_PROPPAGEIDS` macro para declarar el final de la lista de la página de propiedades.  
  
 Para obtener más información sobre páginas de propiedades, vea el artículo [controles ActiveX: páginas de propiedades](../mfc-activex-controls-property-pages.md).  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxctl.h  
   
### <a name="see-also"></a>Vea también   
 [BEGIN_PROPPAGEIDS](#begin_proppageids)   
 [END_PROPPAGEIDS](#end_proppageids)

##  <a name="declare_serial"></a>DECLARE_SERIAL  
 Genera el código de encabezado de C++ necesario para un `CObject`-clase derivada que se puede serializar.  
  
```
DECLARE_SERIAL(class_name)   
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre real de la clase.  
  
### <a name="remarks"></a>Comentarios  
 La serialización es el proceso de escribir o leer el contenido de un objeto a y desde un archivo.  
  
 Use la `DECLARE_SERIAL` macro en un módulo. h y, a continuación, incluir ese módulo en todos los módulos de .cpp que necesitan tener acceso a objetos de esta clase.  
  
 Si `DECLARE_SERIAL` se incluye en la declaración de clase, a continuación, `IMPLEMENT_SERIAL` debe estar incluido en la implementación de la clase.  
  
 El `DECLARE_SERIAL` macro incluye toda la funcionalidad de `DECLARE_DYNAMIC` y `DECLARE_DYNCREATE`.  
  
 Puede usar el **AFX_API** macro para exportar automáticamente la `CArchive` operador de extracción para las clases que utilizan el `DECLARE_SERIAL` y `IMPLEMENT_SERIAL` macros. Corchete de cierre las declaraciones de clase (que se encuentra en el archivo .h) con el código siguiente:  
  
 [!code-cpp[NVC_MFCCObjectSample Nº 20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]  
  
 Para obtener más información sobre la `DECLARE_SERIAL` macro, consulte [temas de la clase de CObject](../../mfc/using-cobject.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCObjectSample #21](../../mfc/codesnippet/cpp/run-time-object-model-services_2.h)]  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="implement_dynamic"></a>IMPLEMENT_DYNAMIC  
 Genera el código de C++ necesario para dinámico `CObject`-deriva la clase con acceso en tiempo de ejecución a las que el nombre de clase y la posición dentro de la jerarquía.  
  
```
IMPLEMENT_DYNAMIC(class_name, base_class_name)  
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre real de la clase.  
  
 `base_class_name`  
 El nombre de la clase base.  
  
### <a name="remarks"></a>Comentarios  
 Use la `IMPLEMENT_DYNAMIC` macro en un módulo .cpp y, a continuación, vínculo el objeto resultante codificar una sola vez.  
  
 Para obtener más información, consulte [temas de la clase de CObject](../../mfc/using-cobject.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCObjectSample n.º 2](../../mfc/codesnippet/cpp/run-time-object-model-services_3.h)]  
  
 [!code-cpp[NVC_MFCCObjectSample 3](../../mfc/codesnippet/cpp/run-time-object-model-services_4.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="implement_dyncreate"></a>IMPLEMENT_DYNCREATE  
 Permite a los objetos de `CObject`-las clases derivadas para crear dinámicamente en ejecución de tiempo cuando se usa con el `DECLARE_DYNCREATE` macro.  
  
```
IMPLEMENT_DYNCREATE(class_name, base_class_name)   
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre real de la clase.  
  
 `base_class_name`  
 El nombre real de la clase base.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo usa esta capacidad para crear la nueva objetos dinámicamente, por ejemplo, cuando lee un objeto desde el disco durante la serialización. Agregar el `IMPLEMENT_DYNCREATE` macro en el archivo de implementación de clase. Para obtener más información, consulte [temas de la clase de CObject](../../mfc/using-cobject.md).  
  
 Si usa el `DECLARE_DYNCREATE` y `IMPLEMENT_DYNCREATE` macros, a continuación, puede usar el `RUNTIME_CLASS` macro y `CObject::IsKindOf` función de miembro para determinar la clase de los objetos en tiempo de ejecución.  
  
 Si `DECLARE_DYNCREATE` se incluye en la declaración de clase, a continuación, `IMPLEMENT_DYNCREATE` debe estar incluido en la implementación de la clase.  
  
 Tenga en cuenta que esta definición de macro va a invocar el constructor predeterminado para la clase. Si la clase se implementa explícitamente un constructor no trivial, explícitamente debe implementar también el constructor predeterminado. El constructor predeterminado puede agregarse a la clase **privada** o **protegido** secciones de miembro para evitar que se llama desde fuera de la implementación de la clase.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCObjectSample #22](../../mfc/codesnippet/cpp/run-time-object-model-services_5.h)]  
  
 [!code-cpp[NVC_MFCCObjectSample #23](../../mfc/codesnippet/cpp/run-time-object-model-services_6.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

## <a name="implement_olecreate_flags"></a>IMPLEMENT_OLECREATE_FLAGS
Cualquier esta macro o [IMPLEMENT_OLECREATE](#implement_olecreate) deben aparecer en el archivo de implementación para cualquier clase que utiliza `DECLARE_OLECREATE`.  
   
### <a name="syntax"></a>Sintaxis    
```
IMPLEMENT_OLECREATE_FLAGS( class_name, external_name, nFlags, 
    l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)  
  
```
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre real de la clase.  
  
 *external_name*  
 El nombre de objeto expuesto a otras aplicaciones (entre comillas).  
  
 `nFlags`  
 Contiene uno o varios de los siguientes indicadores:  
  
-   `afxRegInsertable`Permite el control aparezca en el cuadro de diálogo Insertar objeto para los objetos OLE.    
-   `afxRegApartmentThreading`Establece el modelo de subprocesos en el registro para ThreadingModel = apartamento.    
-   **afxRegFreeThreading** establece el modelo de subprocesos en el registro para ThreadingModel = libre.  
  
     Puede combinar los dos indicadores `afxRegApartmentThreading` y `afxRegFreeThreading` para establecer ThreadingModel = Both. Vea [InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390) en el SDK de Windows para obtener más información sobre el registro del modelo de subprocesos.    
 *l*, *w1*, *w2*, *b1*, *b2*, *b3*, *b4*, *b5*, *b6*, *b7*, *b8*  
 Componentes de la clase **CLSID**.  
   
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Si usa `IMPLEMENT_OLECREATE_FLAGS`, puede especificar qué modelo de subprocesos que sea compatible con el objeto mediante el uso de la `nFlags` parámetro. Si desea admitir solo el modelo solo-Threading, use `IMPLEMENT_OLECREATE`.  
  
 External name es el identificador que se expone a otras aplicaciones. Aplicaciones cliente utilizar el nombre externo para solicitar un objeto de esta clase desde un servidor de automatización.  
  
 El identificador de clase OLE es un identificador único de 128 bits para el objeto. Consta de uno **largo**, dos **WORD**s y ocho **bytes**s, tal como está representada por *l*, *w1*, *w2*, y *b1* a través de *b8* en la descripción de la sintaxis. Los asistentes de Asistente para aplicaciones y código crear Id. de clase OLE único de según sea necesario.  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdisp.h  
   
### <a name="see-also"></a>Vea también  
 [Macros y funciones globales](mfc-macros-and-globals.md)   
 [DECLARE_OLECREATE](#declare_olecreate)   
 [Clave CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424)


## <a name="implement_olecreate"></a>IMPLEMENT_OLECTLTYPE
Implementa el **GetUserTypeNameID** y `GetMiscStatus` las funciones miembro de la clase del control.  
   
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
 Una enumeración que contiene uno o más marcadores. Para obtener más información acerca de esta enumeración, consulte [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497) del SDK de Windows.  
   
### <a name="remarks"></a>Comentarios  
 Además `IMPLEMENT_OLECTLTYPE`, debe agregar el **DECLARE_OLECTLTYPE** macro a la declaración de clase de control.  
  
 El **GetUserTypeNameID** función miembro devuelve la cadena de recurso que identifica la clase del control. `GetMiscStatus`Devuelve el **OLEMISC** bits para el control. Esta enumeración especifica una colección de valores que describen varias características del control. Para obtener una descripción completa de la **OLEMISC** configuración, consulte [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497) del SDK de Windows.  
  
> [!NOTE]
>  La configuración predeterminada utilizada por el ActiveX ControlWizard es: **OLEMISC_ACTIVATEWHENVISIBLE**, **OLEMISC_SETCLIENTSITEFIRST**, **OLEMISC_INSIDEOUT**, **OLEMISC_CANTLINKINSIDE**, y **OLEMISC_RECOMPOSEONRESIZE**.  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxctl.h  
   
### <a name="see-also"></a>Vea también  
 [Macros y funciones globales](mfc-macros-and-globals.md)   
 [DECLARE_OLECTLTYPE](#declare_olectltype)

##  <a name="implement_serial"></a>IMPLEMENT_SERIAL  
 Genera el código de C++ necesario para dinámico `CObject`-deriva la clase con acceso en tiempo de ejecución a las que el nombre de clase y la posición dentro de la jerarquía.  
  
```
IMPLEMENT_SERIAL(class_name, base_class_name, wSchema)  
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre real de la clase.  
  
 `base_class_name`  
 El nombre de la clase base.  
  
 *wSchema*  
 A **UINT** "número de versión" que se va a codificar en el archivo para habilitar un programa deserializar identificar y administrar los datos creados por versiones anteriores versiones de programa. El número de esquema de la clase no debe ser -1.  
  
### <a name="remarks"></a>Comentarios  
 Use la `IMPLEMENT_SERIAL` macro en un módulo .cpp; a continuación, vincule el código objeto resultante de una sola vez.  
  
 Puede usar el **AFX_API** macro para exportar automáticamente la `CArchive` operador de extracción para las clases que utilizan el `DECLARE_SERIAL` y `IMPLEMENT_SERIAL` macros. Corchete de cierre las declaraciones de clase (que se encuentra en el archivo .h) con el código siguiente:  
  
 [!code-cpp[NVC_MFCCObjectSample Nº 20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]  
  
 Para obtener más información, consulte el [temas de la clase de CObject](../../mfc/using-cobject.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCObjectSample #24](../../mfc/codesnippet/cpp/run-time-object-model-services_7.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="runtime_class"></a>RUNTIME_CLASS  
 Obtiene la estructura de clases de tiempo de ejecución desde el nombre de una clase de C++.  
  
```
RUNTIME_CLASS(class_name)  
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre real de la clase (no incluida entre comillas).  
  
### <a name="remarks"></a>Comentarios  
 `RUNTIME_CLASS`Devuelve un puntero a un [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) estructura de la clase especificada por *class_name*. Solo `CObject`-deriva clases declaradas con `DECLARE_DYNAMIC`, `DECLARE_DYNCREATE`, o `DECLARE_SERIAL` devolverá punteros a un `CRuntimeClass` estructura.  
  
 Para obtener más información, consulte [temas de la clase de CObject](../../mfc/using-cobject.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCObjectSample #25](../../mfc/codesnippet/cpp/run-time-object-model-services_8.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 
   
##  <a name="declare_olecreate"></a>DECLARE_OLECREATE  
 Permite a los objetos de `CCmdTarget`-las clases derivadas para crearse a través de automatización OLE.  
  
```
DECLARE_OLECREATE(class_name) 
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre real de la clase.  
  
### <a name="remarks"></a>Comentarios  
 Esta macro permite que otras aplicaciones basadas en OLE crear objetos de este tipo.  
  
 Agregar el `DECLARE_OLECREATE` macro en el módulo .h para la clase y, a continuación, incluir ese módulo en todos los módulos de .cpp que necesitan tener acceso a objetos de esta clase.  
  
 Si `DECLARE_OLECREATE` se incluye en la declaración de clase, a continuación, `IMPLEMENT_OLECREATE` debe estar incluido en la implementación de la clase. Una declaración de clase con `DECLARE_OLECREATE` también debe usar `DECLARE_DYNCREATE` o `DECLARE_SERIAL`.  

### <a name="requirements"></a>Requisitos  
 **Encabezado**: afxdisp.h  

##  <a name="implement_olecreate"></a>IMPLEMENT_OLECREATE  
 Cualquier esta macro o [IMPLEMENT_OLECREATE_FLAGS](http://msdn.microsoft.com/library/d1589f6a-5a69-4742-b07c-4c621cfd040d) deben aparecer en el archivo de implementación para cualquier clase que utiliza `DECLARE_OLECREATE`.  
  
```
IMPLEMENT_OLECREATE(class_name, external_name, l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)  
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre real de la clase.  
  
 *external_name*  
 El nombre de objeto expuesto a otras aplicaciones (entre comillas).  
  
 *l*, *w1*, *w2*, *b1*, *b2*, *b3*, *b4*, *b5*, *b6*, *b7*, *b8*  
 Componentes de la clase **CLSID**.  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Si usa `IMPLEMENT_OLECREATE`, de forma predeterminada, se admite solo el modelo de subprocesamiento único. Si usa `IMPLEMENT_OLECREATE_FLAGS`, puede especificar qué modelo de subprocesos que sea compatible con el objeto mediante el uso de la `nFlags` parámetro.  
  
 External name es el identificador que se expone a otras aplicaciones. Aplicaciones cliente utilizar el nombre externo para solicitar un objeto de esta clase desde un servidor de automatización.  
  
 El identificador de clase OLE es un identificador único de 128 bits para el objeto. Consta de uno **largo**, dos **WORD**s y ocho **bytes**s, tal como está representada por *l*, *w1*, *w2*, y *b1* a través de *b8* en la descripción de la sintaxis. Los asistentes de Asistente para aplicaciones y código crear Id. de clase OLE único de según sea necesario.  

### <a name="requirements"></a>Requisitos  
 **Encabezado**: afxdisp.h 

## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)


