```mermaid
graph LR
    %% 액터 정의
    User((고객))
    Admin((관리자))

    %% 시스템 경계 및 유스케이스 정의
    subgraph 항공예약시스템
        UC_RegCust([고객등록])
        UC_InqCust([고객조회])
        UC_Auth([고객인증])
        UC_InqMile([마일리지조회])
        
        UC_RegFlight([항공권등록])
        UC_InqFlight([항공권조회])
        UC_InqPrice([항공권가격조회])
        
        UC_Reserve([예약])
        UC_InqReserve([예약조회])
        UC_Purchase([구매])
    end

    %% 액터와 기본 유스케이스 연결
    User --- UC_RegCust
    User --- UC_InqCust
    User --- UC_InqFlight
    User --- UC_InqPrice
    User --- UC_Reserve
    User --- UC_InqReserve
    User --- UC_Purchase

    Admin --- UC_RegFlight

    %% 예약 기능의 필수 포함(Include) 관계
    UC_Reserve -. "«include»" .-> UC_Auth
    UC_Reserve -. "«include»" .-> UC_InqFlight

    %% 구매 기능의 필수 포함(Include) 관계
    UC_Purchase -. "«include»" .-> UC_Auth
    UC_Purchase -. "«include»" .-> UC_InqReserve
    UC_Purchase -. "«include»" .-> UC_InqMile