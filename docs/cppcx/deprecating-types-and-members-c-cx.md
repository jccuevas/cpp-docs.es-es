---
title: Dejar en desuso tipos y miembros (C++ / CX) | Documentos de Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: b20b01c1-a439-4ff0-8cf3-d7280c492813
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1cc0ef30006afb9fcad65bc64e3f12fe9586d920
ms.sourcegitcommit: a5a69d2dc3513261e9e28320e4e067aaf40d2ef2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2018
---
# <a name="deprecating-types-and-members-ccx"></a>Dejar en desuso tipos y miembros (C++/CX)
En C++ / CX, degradación de tipos en tiempo de ejecución de Windows y miembros para los productores y consumidores con el [Deprecated](http://msdn.microsoft.com/en-us/8b02ad36-3b5f-4361-888b-e6a99040e57c) se admite el atributo. Si utilizas una API a la que se ha aplicado este atributo, obtienes un mensaje de advertencia en tiempo de compilación que indica que la API está desusada y que te recomienda una API alternativa. Puedes aplicar este atributo en tus propios tipos y métodos públicos, así como proporcionar tus propios mensajes personalizados.  
  
> [!CAUTION]
>  El [Deprecated](http://msdn.microsoft.com/en-us/8b02ad36-3b5f-4361-888b-e6a99040e57c) atributo es para su uso únicamente con tipos en tiempo de ejecución de Windows. En las clases y miembros de C++ estándar, usa [__declspec(deprecated)](http://msdn.microsoft.com/library/044swk7y.aspx).  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo marcar como desusadas tus propias API públicas, por ejemplo, en un componente de Windows en tiempo de ejecución. El segundo parámetro, de tipo [Windows:Foundation::Metadata::DeprecationType](http://msdn.microsoft.com/en-us/ee01e63d-37d0-4273-accc-fca174f88bfa) , especifica si la API se está marcando como desusada o se está quitando. Actualmente, solo se admite el valor DeprecationType::Deprecated. El tercer parámetro del atributo especifica el objeto [Windows::Foundation::Metadata::Platform](http://msdn.microsoft.com/en-us/1eae292d-1ab7-4d97-a58c-b0beffd51ef5) al que se aplica el atributo.  
  
```  
  
namespace wfm = Windows::Foundation::Metadata;  
  
public ref class Bicycle sealed  
{  
  
public:  
    property double Speed;  
  
    [wfm::Deprecated("Use the Speed property to compute the angular speed of the wheel", wfm::DeprecationType::Deprecate, 0x0)]  
    double ComputeAngularVelocity();  
};  
```  
  
## <a name="supported-targets"></a>Destinos admitidos  
 En la tabla siguiente se enumeran las construcciones a las que se puede aplicar el atributo Deprecated:  
  
||  
|-|  
|Control XAML|  
|delegado|  
|evento|  
|campo de enumeración|  
|enum|  
|struct|  
|método|  
|clase|  
|interfaz|  
|propiedad|  
|campo de struct|  
|constructor parametrizado|  
  
## <a name="see-also"></a>Vea también  
 [Sistema de tipos](../cppcx/type-system-c-cx.md)   
 [Referencia del lenguaje de Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)