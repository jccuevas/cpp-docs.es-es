---
title: "system_error (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "system_error/std::system_error"
  - "std.system_error"
  - "std::system_error"
  - "system_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "system_error (clase)"
ms.assetid: 2eeaacbb-8a4a-4ad7-943a-997901a77f32
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# system_error (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Representa la clase base para todas las excepciones para notificar un error del sistema de bajo nivel.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class system_error : public runtime_error {  
public:  
    explicit system_error(error_code _Errcode,
    const string& _Message = "");

    system_error(error_code _Errcode,
    const char *_Message);

    system_error(error_code::value_type _Errval,  
    const error_category& _Errcat,
    const string& _Message);

    system_error(error_code::value_type _Errval,  
    const error_category& _Errcat,
    const char *_Message);
const error_code& code() const throw();
const error_code& code() const throw();

 };  
```  
  
## <a name="remarks"></a>Comentarios  
 El valor devuelto por `what` en la clase [excepción](../standard-library/exception-class1.md) construido a partir de `_Message` y el objeto almacenado de tipo [error_code](../standard-library/error-code-class.md) (ya sea `code` o `error_code(_Errval, _Errcat)`).  
  
 La función miembro `code` devuelve la suma de comprobación [error_code](../standard-library/error-code-class.md) objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \< system_error >  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [\< system_error >](../standard-library/system-error.md)

