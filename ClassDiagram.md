```mermaid
classDiagram
    class Customer {
        +String rrn (주민번호)
        +String password (암호)
        +String name (성명)
        +int mileage (마일리지)
        +register()
        +viewCustomer()
        +authenticate() bool
        +getMileage() int
    }

    class Ticket {
        +String flightId (비행기편)
        +String seat (좌석)
        +String departureTime (출발시간)
        +String arrivalTime (도착시간)
        +int price (항공권가격)
        +registerTicket()
        +viewTicket()
        +getPrice() int
    }

    class Reservation {
        +String reservationId (예약id)
        +String rrn (주민번호)
        +String flightId (비행기편)
        +String seat (좌석)
        +String reservationDate (예약날짜)
        +boolean isPurchased (구매여부)
        +int purchaseCost (구매비용)
        +createReservation(rrn, flightId, seat, date)
        +viewReservation(reservationId)
        +processPurchase(rrn, reservationId) int
    }

    %% 관계 설정
    Customer "1" -- "0..*" Reservation : 예약/구매 수행
    Ticket "1" -- "0..*" Reservation : 예약 대상