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
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 8739201489644b0f1695a70d0dc12d04ca47aa68
ms.lasthandoff: 02/24/2017

---
# <a name="run-time-object-model-services"></a>Servicios del modelo de objetos en tiempo de ejecución
Las clases de [CObject](../../mfc/reference/cobject-class.md) y [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) encapsulan varios servicios de objeto, incluido el acceso a información de clases en tiempo de ejecución, la serialización y la creación dinámica de objetos. Todas las clases derivadas de `CObject` heredan esta funcionalidad.  
  
 Acceso a la información de clase en tiempo de ejecución permite determinar información acerca de la clase de un objeto en tiempo de ejecución. La capacidad para determinar la clase de un objeto en tiempo de ejecución es útil cuando necesita adicional de comprobación de tipos de argumentos de función y cuándo se debe escribir código especial basado en la clase de un objeto. Información de clases en tiempo de ejecución no se admite directamente en el lenguaje C++.  
  
 La serialización es el proceso de escribir o leer el contenido de un objeto a o desde un archivo. Puede utilizar la serialización para almacenar el contenido de un objeto incluso después de salir de la aplicación. El objeto, a continuación, puede leer desde el archivo cuando se reinicia la aplicación. Se dice que estos objetos de datos "persistentes."  
  
 Creación dinámica de objetos le permite crear un objeto de una clase especificada en tiempo de ejecución. Por ejemplo, documento, vista y marco objetos deben admitir la creación dinámica porque el marco de trabajo debe crearlos dinámicamente.  
  
 En la tabla siguiente enumera las macros MFC que admiten la creación dinámica, la serialización y la información de clases en tiempo de ejecución.  
  
 Para obtener más información sobre estos servicios de objeto de tiempo de ejecución y la serialización, vea el artículo [CObject (clase): acceso a la información de clase de tiempo de ejecución](../../mfc/accessing-run-time-class-information.md).  
  
### <a name="run-time-object-model-services-macros"></a>Macros de servicios del modelo de objetos de tiempo de ejecución  
  
|||  
|-|-|  
|[DECLARE_DYNAMIC](#declare_dynamic)|Permite el acceso a la información de clase en tiempo de ejecución (utilizado en la declaración de clase).|  
|[DECLARE_DYNCREATE](#declare_dyncreate)|Permite la creación dinámica y acceso a la información de clase en tiempo de ejecución (utilizado en la declaración de clase).|  
|[DECLARE_SERIAL](#declare_serial)|Permite la serialización y el acceso a la información de clase en tiempo de ejecución (utilizado en la declaración de clase).|  
|[IMPLEMENT_DYNAMIC](#implement_dynamic)|Permite el acceso a la información de clase en tiempo de ejecución (debe utilizarse en la implementación de la clase).|  
|[IMPLEMENT_DYNCREATE](#implement_dyncreate)|Permite la creación dinámica y acceso a la información de tiempo de ejecución (debe utilizarse en la implementación de la clase).|  
|[IMPLEMENT_SERIAL](#implement_serial)|Permite la serialización y el acceso a la información de clase en tiempo de ejecución (debe utilizarse en la implementación de la clase).|  
|[RUNTIME_CLASS](#runtime_class)|Devuelve el `CRuntimeClass` estructura que corresponde a la clase con nombre.|  


 OLE con frecuencia requiere la creación dinámica de objetos en tiempo de ejecución. Por ejemplo, una aplicación de servidor OLE debe ser capaz de crear elementos OLE dinámicamente en respuesta a una solicitud de un cliente. De forma similar, un servidor de automatización debe ser capaz de crear elementos en respuesta a las solicitudes de los clientes de automatización.  
  
 La biblioteca Microsoft Foundation Class proporciona dos macros específicas OLE.  
  
### <a name="dynamic-creation-of-ole-objects"></a>Creación dinámica de objetos OLE  
  
|||  
|-|-|  
|[DECLARE_OLECREATE](#declare_olecreate)|Permite a los objetos que se crearán mediante la automatización OLE.|  
|[IMPLEMENT_OLECREATE](#implement_olecreate)|Permite a los objetos que va a crear el sistema OLE.|  
  
##  <a name="a-namedeclaredynamica--declaredynamic"></a><a name="declare_dynamic"></a>DECLARE_DYNAMIC  
 Agrega la capacidad de tener acceso a información de tiempo de ejecución acerca de la clase de un objeto al derivar una clase de `CObject`.  
  
```
DECLARE_DYNAMIC(class_name) 
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre real de la clase.  
  
### <a name="remarks"></a>Comentarios  
 Agregue el `DECLARE_DYNAMIC` macro para el módulo de encabezado (. h) para la clase, a continuación, incluya ese módulo en todos los módulos .cpp que necesitan tener acceso a objetos de esta clase.  
  
 Si utiliza la **DECLARE**_ **dinámica** y `IMPLEMENT_DYNAMIC` macros tal como se describe a continuación, puede utilizar el `RUNTIME_CLASS` macro y `CObject::IsKindOf` función para determinar la clase de los objetos en tiempo de ejecución.  
  
 Si `DECLARE_DYNAMIC` se incluye en la declaración de clase, `IMPLEMENT_DYNAMIC` debe estar incluido en la implementación de la clase.  
  
 Para obtener más información sobre la `DECLARE_DYNAMIC` (macro), consulte [temas de la clase de CObject](../../mfc/using-cobject.md).  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [IMPLEMENT_DYNAMIC](#implement_dynamic).  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="a-namedeclaredyncreatea--declaredyncreate"></a><a name="declare_dyncreate"></a>DECLARE_DYNCREATE  
 Permite a los objetos de `CObject`-las clases derivadas para crear dinámicamente en tiempo de ejecución.  
  
```
DECLARE_DYNCREATE(class_name)   
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre real de la clase.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo utiliza esta capacidad para crear nuevos objetos de forma dinámica. Por ejemplo, la nueva vista creada cuando se abre un nuevo documento. Clases de marco, vista y documento deben admitir la creación dinámica porque el marco de trabajo debe crearlos dinámicamente.  
  
 Agregue el `DECLARE_DYNCREATE` macro del módulo .h para la clase, a continuación, incluya ese módulo en todos los módulos .cpp que necesitan tener acceso a objetos de esta clase.  
  
 Si `DECLARE_DYNCREATE` se incluye en la declaración de clase, `IMPLEMENT_DYNCREATE` debe estar incluido en la implementación de la clase.  
  
 Para obtener más información sobre la `DECLARE_DYNCREATE` (macro), consulte [temas de la clase de CObject](../../mfc/using-cobject.md).  
  
> [!NOTE]
>  El `DECLARE_DYNCREATE` macro incluye toda la funcionalidad de `DECLARE_DYNAMIC`.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [IMPLEMENT_DYNCREATE](#implement_dyncreate).  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="a-namedeclareseriala--declareserial"></a><a name="declare_serial"></a>DECLARE_SERIAL  
 Genera el código de encabezado de C++ necesario para un `CObject`-clase derivada que se puede serializar.  
  
```
DECLARE_SERIAL(class_name)   
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre real de la clase.  
  
### <a name="remarks"></a>Comentarios  
 La serialización es el proceso de escribir o leer el contenido de un objeto a y desde un archivo.  
  
 Utilice la `DECLARE_SERIAL` macro en un módulo. h y, a continuación, incluya ese módulo en todos los módulos .cpp que necesitan tener acceso a objetos de esta clase.  
  
 Si `DECLARE_SERIAL` se incluye en la declaración de clase, `IMPLEMENT_SERIAL` debe estar incluido en la implementación de la clase.  
  
 El `DECLARE_SERIAL` macro incluye toda la funcionalidad de `DECLARE_DYNAMIC` y `DECLARE_DYNCREATE`.  
  
 Puede usar el **AFX_API** macro para exportar automáticamente la `CArchive` operador de extracción para las clases que utilizan la `DECLARE_SERIAL` y `IMPLEMENT_SERIAL` macros. Corchete de cierre las declaraciones de clase (que se encuentra en el archivo .h) con el código siguiente:  
  
 [!code-cpp[NVC_MFCCObjectSample&#20;](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]  
  
 Para obtener más información sobre la `DECLARE_SERIAL` (macro), consulte [temas de la clase de CObject](../../mfc/using-cobject.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[21 NVC_MFCCObjectSample](../../mfc/codesnippet/cpp/run-time-object-model-services_2.h)]  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="a-nameimplementdynamica--implementdynamic"></a><a name="implement_dynamic"></a>IMPLEMENT_DYNAMIC  
 Genera el código de C++ necesario para una dinámica `CObject`-derivado de clase con acceso en tiempo de ejecución para el nombre de clase y la posición dentro de la jerarquía.  
  
```
IMPLEMENT_DYNAMIC(class_name, base_class_name)  
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre real de la clase.  
  
 `base_class_name`  
 El nombre de la clase base.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la `IMPLEMENT_DYNAMIC` macro en un módulo .cpp y, a continuación, vincular el objeto resultante código sólo una vez.  
  
 Para obtener más información, consulte [temas de la clase de CObject](../../mfc/using-cobject.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCObjectSample&#2;](../../mfc/codesnippet/cpp/run-time-object-model-services_3.h)]  
  
 [!code-cpp[NVC_MFCCObjectSample&3;](../../mfc/codesnippet/cpp/run-time-object-model-services_4.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="a-nameimplementdyncreatea--implementdyncreate"></a><a name="implement_dyncreate"></a>IMPLEMENT_DYNCREATE  
 Permite a los objetos de `CObject`-a se crean dinámicamente en ejecución las clases derivadas de tiempo cuando se usa con el `DECLARE_DYNCREATE` (macro).  
  
```
IMPLEMENT_DYNCREATE(class_name, base_class_name)   
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre real de la clase.  
  
 `base_class_name`  
 El nombre real de la clase base.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo utiliza esta capacidad para crear la nueva objetos dinámicamente, por ejemplo, cuando lee un objeto desde el disco durante la serialización. Agregue el `IMPLEMENT_DYNCREATE` macro en el archivo de implementación de la clase. Para obtener más información, consulte [temas de la clase de CObject](../../mfc/using-cobject.md).  
  
 Si utiliza la `DECLARE_DYNCREATE` y `IMPLEMENT_DYNCREATE` macros, puede utilizar el `RUNTIME_CLASS` macro y `CObject::IsKindOf` función miembro para determinar la clase de los objetos en tiempo de ejecución.  
  
 Si `DECLARE_DYNCREATE` se incluye en la declaración de clase, `IMPLEMENT_DYNCREATE` debe estar incluido en la implementación de la clase.  
  
 Tenga en cuenta que esta definición de macro invocará el constructor predeterminado para la clase. Si la clase se implementa explícitamente un constructor no trivial, explícitamente debe implementar también el constructor predeterminado. El constructor predeterminado se puede agregar a la clase **privada** o **protegido** secciones de miembro para evitar que se va a llamar desde fuera de la implementación de la clase.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCObjectSample&#22;](../../mfc/codesnippet/cpp/run-time-object-model-services_5.h)]  
  
 [!code-cpp[23 de NVC_MFCCObjectSample #](../../mfc/codesnippet/cpp/run-time-object-model-services_6.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="a-nameimplementseriala--implementserial"></a><a name="implement_serial"></a>IMPLEMENT_SERIAL  
 Genera el código de C++ necesario para una dinámica `CObject`-derivado de clase con acceso en tiempo de ejecución para el nombre de clase y la posición dentro de la jerarquía.  
  
```
IMPLEMENT_SERIAL(class_name, base_class_name, wSchema)  
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre real de la clase.  
  
 `base_class_name`  
 El nombre de la clase base.  
  
 *wSchema*  
 Un **UINT** "número de versión" que se va a codificar en el archivo que se va a habilitar un programa de deserialización identificar y tratar los datos creados por versiones anteriores versiones de programa. El número de esquema de clase no debe ser â €"1.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la `IMPLEMENT_SERIAL` macro en un módulo .cpp; a continuación, vincular el código objeto resultante sólo una vez.  
  
 Puede usar el **AFX_API** macro para exportar automáticamente la `CArchive` operador de extracción para las clases que utilizan la `DECLARE_SERIAL` y `IMPLEMENT_SERIAL` macros. Corchete de cierre las declaraciones de clase (que se encuentra en el archivo .h) con el código siguiente:  
  
 [!code-cpp[NVC_MFCCObjectSample&#20;](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]  
  
 Para obtener más información, consulte el [temas de la clase de CObject](../../mfc/using-cobject.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCObjectSample&#24;](../../mfc/codesnippet/cpp/run-time-object-model-services_7.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 

##  <a name="a-nameruntimeclassa--runtimeclass"></a><a name="runtime_class"></a>RUNTIME_CLASS  
 Obtiene la estructura de clases de tiempo de ejecución desde el nombre de una clase de C++.  
  
```
RUNTIME_CLASS(class_name)  
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre real de la clase (no está entre comillas).  
  
### <a name="remarks"></a>Comentarios  
 `RUNTIME_CLASS`Devuelve un puntero a un [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) estructura de la clase especificada por *class_name*. Sólo `CObject`-derivadas de clases declaradas con `DECLARE_DYNAMIC`, `DECLARE_DYNCREATE`, o `DECLARE_SERIAL` devolverá punteros a un `CRuntimeClass` estructura.  
  
 Para obtener más información, consulte [temas de la clase de CObject](../../mfc/using-cobject.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCCObjectSample&#25;](../../mfc/codesnippet/cpp/run-time-object-model-services_8.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h 
   
##  <a name="a-namedeclareolecreatea--declareolecreate"></a><a name="declare_olecreate"></a>DECLARE_OLECREATE  
 Permite a los objetos de `CCmdTarget`-las clases derivadas para crear mediante la automatización OLE.  
  
```
DECLARE_OLECREATE(class_name) 
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre real de la clase.  
  
### <a name="remarks"></a>Comentarios  
 Esta macro permite que otras aplicaciones OLE crear objetos de este tipo.  
  
 Agregue el `DECLARE_OLECREATE` macro del módulo .h para la clase y, a continuación, incluya ese módulo en todos los módulos .cpp que necesitan tener acceso a objetos de esta clase.  
  
 Si `DECLARE_OLECREATE` se incluye en la declaración de clase, `IMPLEMENT_OLECREATE` debe estar incluido en la implementación de la clase. Una declaración de clase mediante `DECLARE_OLECREATE` también debe usar `DECLARE_DYNCREATE` o `DECLARE_SERIAL`.  

### <a name="requirements"></a>Requisitos  
 **Encabezado**: afxdisp.h  

##  <a name="a-nameimplementolecreatea--implementolecreate"></a><a name="implement_olecreate"></a>IMPLEMENT_OLECREATE  
 En esta macro o [IMPLEMENT_OLECREATE_FLAGS](http://msdn.microsoft.com/library/d1589f6a-5a69-4742-b07c-4c621cfd040d) debe aparecer en el archivo de implementación para cualquier clase que utiliza `DECLARE_OLECREATE`.  
  
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
>  Si usa `IMPLEMENT_OLECREATE`, de forma predeterminada, admite sólo el modelo de subprocesamiento único. Si utiliza `IMPLEMENT_OLECREATE_FLAGS`, puede especificar qué modelo de subprocesamiento que admite el objeto mediante el `nFlags` parámetro.  
  
 External name es el identificador que se expone a otras aplicaciones. Aplicaciones cliente utilizar el nombre externo para solicitar un objeto de esta clase desde un servidor de automatización.  
  
 El identificador de clase OLE es un identificador único de 128 bits para el objeto. Consta de uno **largo**, dos **WORD**s y ocho **bytes**s, representados por *l*, *w1*, *w2*, y *b1* a través de *M8* en la descripción de sintaxis. Los asistentes de Asistente para aplicaciones y código para crean identificadores únicos de clases OLE de según sea necesario.  

### <a name="requirements"></a>Requisitos  
 **Encabezado**: afxdisp.h 

## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)

