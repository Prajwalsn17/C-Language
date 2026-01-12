flowchart LR

    %% =========================
    %% Nodes
    %% =========================
    ESP32
    RELAY[2-Channel Relay Module]
    FEEDER[Feeder (5V Supply)]
    CAN[CAN Module]
    CANBUS[Another CAN Module]

    %% =========================
    %% ESP32 → Relay Connections
    %% =========================
    ESP32 -->|Vcc| RELAY
    ESP32 -->|GND| RELAY
    ESP32 -->|GPIO 25 (IN1)| RELAY
    ESP32 -->|GPIO 26 (IN2)| RELAY

    %% =========================
    %% ESP32 → CAN Connections
    %% =========================
    ESP32 -->|Vcc| CAN
    ESP32 -->|GND| CAN
    ESP32 -->|TX| CAN
    ESP32 -->|RX| CAN

    %% =========================
    %% Relay → Feeder Connections
    %% =========================
    RELAY -->|NO| FEEDER
    RELAY -->|COM| FEEDER

    %% =========================
    %% CAN Bus Connections
    %% =========================
    CAN -->|CAN_H| CANBUS
    CAN -->|CAN_L| CANBUS
