---
title: "CRegKey Class | Microsoft Docs"
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
  - "CRegKey"
  - "ATL::CRegKey"
  - "ATL.CRegKey"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, Registro"
  - "CRegKey class"
  - "Registro, eliminar claves"
  - "Registro, eliminar valores"
  - "Registro, escribir"
ms.assetid: 3afce82b-ba2c-4c1a-8404-dc969e1af74b
caps.latest.revision: 25
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRegKey Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para manipular entradas en el registro del sistema.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class CRegKey  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRegKey::CRegKey](../Topic/CRegKey::CRegKey.md)|el constructor.|  
|[CRegKey::~CRegKey](../Topic/CRegKey::~CRegKey.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRegKey::Attach](../Topic/CRegKey::Attach.md)|Llame a este método para asociar un HKEY al objeto de `CRegKey` estableciendo el identificador del miembro de [m\_hKey](../Topic/CRegKey::m_hKey.md) a `hKey`.|  
|[CRegKey::Close](../Topic/CRegKey::Close.md)|Llame a este método para liberar el identificador del miembro de [m\_hKey](../Topic/CRegKey::m_hKey.md) y para establecerlo en NULL.|  
|[CRegKey::Create](../Topic/CRegKey::Create.md)|Llame a este método para crear la clave especificada, si no existe como subclave de `hKeyParent`.|  
|[CRegKey::DeleteSubKey](../Topic/CRegKey::DeleteSubKey.md)|Llame a este método para quitar la clave especificada del registro.|  
|[CRegKey::DeleteValue](../Topic/CRegKey::DeleteValue.md)|Llame a este método para quitar un campo de Valor de [m\_hKey](../Topic/CRegKey::m_hKey.md).|  
|[CRegKey::Detach](../Topic/CRegKey::Detach.md)|Llame a este método para desasociar el identificador del miembro de [m\_hKey](../Topic/CRegKey::m_hKey.md) del objeto de `CRegKey` y `m_hKey` determinado en NULL.|  
|[CRegKey::EnumKey](../Topic/CRegKey::EnumKey.md)|Llame a este método para enumerar las subclaves de la clave del Registro abierto.|  
|[CRegKey::Flush](../Topic/CRegKey::Flush.md)|Llame a este método para escribir todos los atributos de clave del Registro abierto en el registro.|  
|[CRegKey::GetKeySecurity](../Topic/CRegKey::GetKeySecurity.md)|Llame a este método para recuperar una copia del descriptor de seguridad que protege la clave del Registro abierto.|  
|[CRegKey::NotifyChangeKeyValue](../Topic/CRegKey::NotifyChangeKeyValue.md)|Este método notifica al llamador sobre cambios en los atributos o al contenido de clave del Registro abierto.|  
|[CRegKey::Open](../Topic/CRegKey::Open.md)|Llame a este método para abrir la clave especificada y [m\_hKey](../Topic/CRegKey::m_hKey.md) determinado en el identificador de esta clave.|  
|[CRegKey::QueryBinaryValue](../Topic/CRegKey::QueryBinaryValue.md)|Llame a este método para recuperar los datos binarios de un nombre de valor especificado.|  
|[CRegKey::QueryDWORDValue](../Topic/CRegKey::QueryDWORDValue.md)|Llame a este método para recuperar los datos de DWORD para un nombre de valor especificado.|  
|[CRegKey::QueryGUIDValue](../Topic/CRegKey::QueryGUIDValue.md)|Llame a este método para recuperar los datos del GUID para un nombre de valor especificado.|  
|[CRegKey::QueryMultiStringValue](../Topic/CRegKey::QueryMultiStringValue.md)|Llame a este método para recuperar los datos multistring para un nombre de valor especificado.|  
|[CRegKey::QueryQWORDValue](../Topic/CRegKey::QueryQWORDValue.md)|Llame a este método para recuperar los datos de QWORD para un nombre de valor especificado.|  
|[CRegKey::QueryStringValue](../Topic/CRegKey::QueryStringValue.md)|Llame a este método para recuperar los datos de cadena para un nombre de valor especificado.|  
|[CRegKey::QueryValue](../Topic/CRegKey::QueryValue.md)|Llame a este método para recuperar los datos del campo de valor especificado de [m\_hKey](../Topic/CRegKey::m_hKey.md).  Versiones anteriores de este método se admiten y se marcan ya no como **ATL\_DEPRECATED**.|  
|[CRegKey::RecurseDeleteKey](../Topic/CRegKey::RecurseDeleteKey.md)|Llame a este método para quitar la clave especificada del registro y explícitamente para quitar cualquier subclave.|  
|[CRegKey::SetBinaryValue](../Topic/CRegKey::SetBinaryValue.md)|Llame a este método para establecer el valor binario de la clave del Registro.|  
|[CRegKey::SetDWORDValue](../Topic/CRegKey::SetDWORDValue.md)|Llame a este método para establecer el valor DWORD de la clave del Registro.|  
|[CRegKey::SetGUIDValue](../Topic/CRegKey::SetGUIDValue.md)|Llame a este método para establecer el valor de GUID de la clave del Registro.|  
|[CRegKey::SetKeySecurity](../Topic/CRegKey::SetKeySecurity.md)|Llame a este método para establecer la seguridad de la clave del Registro.|  
|[CRegKey::SetKeyValue](../Topic/CRegKey::SetKeyValue.md)|Llame a este método para almacenar datos en un campo de valor especificado de una clave especificada.|  
|[CRegKey::SetMultiStringValue](../Topic/CRegKey::SetMultiStringValue.md)|Llame a este método para establecer el valor multistring de la clave del Registro.|  
|[CRegKey::SetQWORDValue](../Topic/CRegKey::SetQWORDValue.md)|Llame a este método para establecer el valor de QWORD de la clave del Registro.|  
|[CRegKey::SetStringValue](../Topic/CRegKey::SetStringValue.md)|Llame a este método para establecer el valor de cadena de la clave del Registro.|  
|[CRegKey::SetValue](../Topic/CRegKey::SetValue.md)|Llame a este método para almacenar datos en el campo de valor especificado de [m\_hKey](../Topic/CRegKey::m_hKey.md).  Versiones anteriores de este método se admiten y se marcan ya no como **ATL\_DEPRECATED**.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRegKey::operator HKEY](../Topic/CRegKey::operator%20HKEY.md)|convierte un objeto de `CRegKey` a un HKEY.|  
|[CRegKey::operator \=](../Topic/CRegKey::operator%20=.md)|Operador de asignación.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRegKey::m\_hKey](../Topic/CRegKey::m_hKey.md)|Contiene un identificador de clave de Registro asociado al objeto de `CRegKey` .|  
|[CRegKey::m\_pTM](../Topic/CRegKey::m_pTM.md)|Puntero al objeto de `CAtlTransactionManager`|  
  
## Comentarios  
 `CRegKey` proporciona métodos para crear y eliminar claves y valores del sistema.  El registro contiene un conjunto instalación\- específico de definiciones para los componentes del sistema, como números de versión de software, asignaciones lógico\-a\- físicas de hardware instalado, y objetos COM.  
  
 `CRegKey` proporciona una interfaz de programación al registro del sistema para un equipo determinado.  Por ejemplo, abrir un clave de Registro concreto, llamada `CRegKey::Open`.  Para recuperar o modificar un valor de datos, una llamada `CRegKey::QueryValue` o `CRegKey::SetValue`, respectivamente.  Para cerrar una clave, llame a `CRegKey::Close`.  
  
 Al cerrar una clave, los datos del Registro escriben \(vaciado\) en el disco duro.  Este proceso puede tardar varios segundos.  Si su aplicación debe explícitamente escribir datos del Registro en el disco duro, puede llamar a la función de [RegFlushKey](http://msdn.microsoft.com/library/windows/desktop/ms724867) Win32.  Sin embargo, **RegFlushKey** utiliza muchos recursos del sistema y debe invocarse únicamente cuando sea absolutamente necesario.  
  
> [!IMPORTANT]
>  Cualquier método que permite que el llamador especifique una ubicación del registro tiene el potencial para leer datos que no se han confirmado.  Los métodos que utilizan de [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) deben tener en cuenta que esta función no controla las cadenas que son NULL finalizados.  Ambas condiciones deben comprobar para el código de llamada.  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Vea también  
 [Ejemplo DCOM](../../top/visual-cpp-samples.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Registry Overview](http://msdn.microsoft.com/library/windows/desktop/ms724871)   
 [Registry Functions](http://msdn.microsoft.com/library/windows/desktop/ms724875)   
 [Registry Value Types](http://msdn.microsoft.com/library/windows/desktop/ms724884)