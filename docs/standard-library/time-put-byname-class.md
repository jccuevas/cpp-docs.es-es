---
title: time_put_byname (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- time_put_byname
- xloctime/std::time_put_byname
dev_langs:
- C++
helpviewer_keywords:
- time_put_byname class
ms.assetid: e08c2348-64d2-4ace-98b1-1496e14c7b1a
caps.latest.revision: 25
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: a21c91fba99623ae7c97ef1455278617746fc310
ms.contentlocale: es-es
ms.lasthandoff: 04/29/2017

---
# <a name="timeputbyname-class"></a>time_put_byname (Clase)
Una clase de plantilla derivada que describe un objeto que puede actuar como una faceta de configuración regional de tipo `time_put`\< CharType, OutputIterator >.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class CharType, class OutIt = ostreambuf_iterator<CharType, char_traits<CharType>>>
class time_put_byname : public time_put<CharType, OutputIterator>
{
public:
    explicit time_put_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit time_put_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~time_put_byname();

};
```  
  
#### <a name="parameters"></a>Parámetros  
 `_Locname`  
 Un nombre de configuración regional.  
  
 `_Refs`  
 Un recuento de referencias inicial.  
  
## <a name="remarks"></a>Comentarios  
 Su comportamiento viene determinado por la configuración regional [con nombre](../standard-library/locale-class.md#name) `_Locname`. Cada constructor inicializa su objeto base con [time_put](../standard-library/time-put-class.md#time_put)\<CharType, OutputIterator>( `_Refs`).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<locale>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)




