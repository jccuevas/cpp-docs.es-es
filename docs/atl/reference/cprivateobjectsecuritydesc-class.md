---
title: Clase CPrivateObjectSecurityDesc | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CPrivateObjectSecurityDesc
- ATL::CPrivateObjectSecurityDesc
- CPrivateObjectSecurityDesc
dev_langs:
- C++
helpviewer_keywords:
- CPrivateObjectSecurityDesc class
ms.assetid: 2c4bbb13-bf99-4833-912a-197f6815bb5d
caps.latest.revision: 20
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 154a4229f8963d3081e6e0518354d17968ee0e20
ms.lasthandoff: 02/24/2017

---
# <a name="cprivateobjectsecuritydesc-class"></a>Clase CPrivateObjectSecurityDesc
Esta clase representa un objeto de descriptor de seguridad de objeto privado.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CPrivateObjectSecurityDesc : public CSecurityDesc
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc](#cprivateobjectsecuritydesc)|El constructor.|  
|[CPrivateObjectSecurityDesc:: ~ CPrivateObjectSecurityDesc](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPrivateObjectSecurityDesc::ConvertToAutoInherit](#converttoautoinherit)|Llamar a este método para convertir un descriptor de seguridad y las listas de control de acceso (ACL) en un formato compatible con la propagación automática de entradas de control de acceso heredables (ACE).|  
|[CPrivateObjectSecurityDesc::Create](#create)|Llame a este método para asignar e inicializar un descriptor de seguridad autorelativo para el objeto privado creado por el Administrador de recursos que realiza la llamada.|  
|[CPrivateObjectSecurityDesc::Get](#get)|Llamar a este método para recuperar información del descriptor de seguridad de un objeto privado.|  
|[CPrivateObjectSecurityDesc::Set](#set)|Llamar a este método para modificar el descriptor de seguridad de un objeto privado.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operador =](#operator_eq)|Operador de asignación.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase deriva de [CSecurityDesc](../../atl/reference/csecuritydesc-class.md), proporciona métodos para crear y administrar el descriptor de seguridad de un objeto privado.  
  
 Para obtener una introducción al modelo de control de acceso de Windows, consulte [de Control de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374860) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CSecurityDesc](../../atl/reference/csecuritydesc-class.md)  
  
 `CPrivateObjectSecurityDesc`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsecurity.h  
  
##  <a name="a-nameconverttoautoinherita--cprivateobjectsecuritydescconverttoautoinherit"></a><a name="converttoautoinherit"></a>CPrivateObjectSecurityDesc::ConvertToAutoInherit  
 Llamar a este método para convertir un descriptor de seguridad y las listas de control de acceso (ACL) en un formato compatible con la propagación automática de entradas de control de acceso heredables (ACE).  
  
```
bool ConvertToAutoInherit(  
    const CSecurityDesc* pParent,
    GUID* ObjectType,
    bool bIsDirectoryObject,
    PGENERIC_MAPPING GenericMapping) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pParent`  
 Puntero a un [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) objeto que hace referencia el contenedor primario del objeto. Si no hay ningún contenedor primario, este parámetro es NULL.  
  
 `ObjectType`  
 Puntero a un **GUID** estructura que identifica el tipo de objeto asociado con el objeto actual. Establecer `ObjectType` como NULL si el objeto no tiene un GUID.  
  
 `bIsDirectoryObject`  
 Especifica si el nuevo objeto puede contener otros objetos. Un valor de true indica que el nuevo objeto es un contenedor. Un valor de false indica que el nuevo objeto no es un contenedor.  
  
 `GenericMapping`  
 Puntero a un [GENERIC_MAPPING](http://msdn.microsoft.com/library/windows/desktop/aa446633) estructura que especifica la asignación de cada derecho a derechos específicos para el objeto genérico.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 Este método intenta determinar si la lista de las ACE en el control de acceso discrecional (DACL) y una lista de control de acceso de sistema (SACL) del descriptor de seguridad actual se heredan de descriptor de seguridad del elemento primario. Llama a la [ConvertToAutoInheritPrivateObjectSecurity](http://msdn.microsoft.com/library/windows/desktop/aa376403) (función).  
  
##  <a name="a-namecprivateobjectsecuritydesca--cprivateobjectsecuritydesccprivateobjectsecuritydesc"></a><a name="cprivateobjectsecuritydesc"></a>CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc  
 El constructor.  
  
```
CPrivateObjectSecurityDesc() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Inicializa el `CPrivateObjectSecurityDesc` objeto.  
  
##  <a name="a-namedtora--cprivateobjectsecuritydesccprivateobjectsecuritydesc"></a><a name="dtor"></a>CPrivateObjectSecurityDesc:: ~ CPrivateObjectSecurityDesc  
 Destructor.  
  
```
~CPrivateObjectSecurityDesc() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 El destructor libera todos los recursos asignados y elimina el descriptor de seguridad del objeto privado.  
  
##  <a name="a-namecreatea--cprivateobjectsecuritydesccreate"></a><a name="create"></a>CPrivateObjectSecurityDesc::Create  
 Llame a este método para asignar e inicializar un descriptor de seguridad autorelativo para el objeto privado creado por el Administrador de recursos que realiza la llamada.  
  
```
bool Create(  
    const CSecurityDesc* pParent,
    const CSecurityDesc* pCreator,
    bool bIsDirectoryObject,
    const CAccessToken& Token,
    PGENERIC_MAPPING GenericMapping) throw();

bool Create(  
    const CSecurityDesc* pParent,
    const CSecurityDesc* pCreator,
    GUID* ObjectType,
    bool bIsContainerObject,
    ULONG AutoInheritFlags,
    const CAccessToken& Token,
    PGENERIC_MAPPING GenericMapping) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pParent`  
 Puntero a un [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) objeto que hace referencia el directorio principal en el que se se crea un nuevo objeto. Se establece en NULL si no hay ningún directorio primario.  
  
 `pCreator`  
 Puntero a un descriptor de seguridad proporcionado por el creador del objeto. Si el creador del objeto explícitamente no pasa la información de seguridad para el nuevo objeto, establezca este parámetro en NULL.  
  
 `bIsDirectoryObject`  
 Especifica si el nuevo objeto puede contener otros objetos. Un valor de true indica que el nuevo objeto es un contenedor. Un valor de false indica que el nuevo objeto no es un contenedor.  
  
 `Token`  
 Hacer referencia a la [CAccessToken](../../atl/reference/caccesstoken-class.md) objeto para el proceso del cliente en cuyo nombre se va a crear el objeto.  
  
 `GenericMapping`  
 Puntero a un [GENERIC_MAPPING](http://msdn.microsoft.com/library/windows/desktop/aa446633) estructura que especifica la asignación de cada derecho a derechos específicos para el objeto genérico.  
  
 `ObjectType`  
 Puntero a un **GUID** estructura que identifica el tipo de objeto asociado con el objeto actual. Establecer `ObjectType` como NULL si el objeto no tiene un GUID.  
  
 *bIsContainerObject*  
 Especifica si el nuevo objeto puede contener otros objetos. Un valor de true indica que el nuevo objeto es un contenedor. Un valor de false indica que el nuevo objeto no es un contenedor.  
  
 `AutoInheritFlags`  
 Un conjunto de marcadores de bits que controlan cómo se heredan las entradas de control de acceso (ACE) de `pParent`. Consulte [CreatePrivateObjectSecurityEx](http://msdn.microsoft.com/library/windows/desktop/aa446581) para obtener más detalles.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 Este método llama a [CreatePrivateObjectSercurity](http://msdn.microsoft.com/library/windows/desktop/aa376405) o [CreatePrivateObjectSecurityEx](http://msdn.microsoft.com/library/windows/desktop/aa446581).  
  
 El segundo método, que permite especificar el tipo de objeto GUID del nuevo objeto o controlar cómo se heredan las ACE, sólo está disponible en sistemas que ejecutan Windows 2000 y versiones posteriores.  
  
> [!NOTE]
>  Un descriptor de seguridad autorelativo es un descriptor de seguridad que almacena toda la información de seguridad en un bloque de memoria contiguo.  
  
##  <a name="a-namegeta--cprivateobjectsecuritydescget"></a><a name="get"></a>CPrivateObjectSecurityDesc::Get  
 Llamar a este método para recuperar información del descriptor de seguridad de un objeto privado.  
  
```
bool Get(  
    SECURITY_INFORMATION si,
    CSecurityDesc* pResult) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `si`  
 Un conjunto de marcadores de bits que indican las partes del descriptor de seguridad para recuperar. Este valor puede ser una combinación de la [SECURITY_INFORMATION](http://msdn.microsoft.com/library/windows/desktop/aa379573) marcadores de bits.  
  
 `pResult`  
 Puntero a un [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) objeto que recibe una copia de la información solicitada del descriptor de seguridad especificado.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 El descriptor de seguridad es una estructura y datos asociados que contiene la información de seguridad para un objeto asegurable.  
  
##  <a name="a-nameoperatoreqa--cprivateobjectsecuritydescoperator-"></a><a name="operator_eq"></a>CPrivateObjectSecurityDesc::operator =  
 Operador de asignación.  
  
```
CPrivateObjectSecurityDesc& operator= (const CPrivateObjectSecurityDesc& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `rhs`  
 La `CPrivateObjectSecurityDesc` objeto que se va a asignar al objeto actual.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el texto actualizado `CPrivateObjectSecurityDesc` objeto.  
  
##  <a name="a-nameseta--cprivateobjectsecuritydescset"></a><a name="set"></a>CPrivateObjectSecurityDesc::Set  
 Llamar a este método para modificar el descriptor de seguridad de un objeto privado.  
  
```
bool Set(  
    SECURITY_INFORMATION si,
    const CSecurityDesc& Modification,
    PGENERIC_MAPPING GenericMapping,
    const CAccessToken& Token) throw();

bool Set(  
    SECURITY_INFORMATION si,
    const CSecurityDesc& Modification,
    ULONG AutoInheritFlags,
    PGENERIC_MAPPING GenericMapping,
    const CAccessToken& Token) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `si`  
 Un conjunto de marcadores de bits que indican las partes del descriptor de seguridad para establecer. Este valor puede ser una combinación de la [SECURITY_INFORMATION](http://msdn.microsoft.com/library/windows/desktop/aa379573) marcadores de bits.  
  
 *Modificación*  
 Puntero a un [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) objeto. Las partes de este descriptor de seguridad indican por el `si` parámetro se aplica al descriptor de seguridad del objeto.  
  
 `GenericMapping`  
 Puntero a un [GENERIC_MAPPING](http://msdn.microsoft.com/library/windows/desktop/aa446633) estructura que especifica la asignación de cada derecho a derechos específicos para el objeto genérico.  
  
 `Token`  
 Hacer referencia a la [CAccessToken](../../atl/reference/caccesstoken-class.md) objeto para el proceso del cliente en cuyo nombre se va a crear el objeto.  
  
 `AutoInheritFlags`  
 Un conjunto de marcadores de bits que controlan cómo se heredan las entradas de control de acceso (ACE) de `pParent`. Consulte [CreatePrivateObjectSecurityEx](http://msdn.microsoft.com/library/windows/desktop/aa446581) para obtener más detalles.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 El segundo método, que permite especificar el GUID del tipo de objeto del objeto o controlar cómo se heredan las ACE, sólo está disponible en sistemas que ejecutan Windows 2000 y versiones posteriores.  
  
## <a name="see-also"></a>Vea también  
 [SECURITY_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [Información general de la clase](../../atl/atl-class-overview.md)   
 [Funciones globales de seguridad](../../atl/reference/security-global-functions.md)   
 [Clase CSecurityDesc](../../atl/reference/csecuritydesc-class.md)

