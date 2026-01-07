import gradio as gradio
import time

def check_identity(user_input, start_time):
    # คำนวณเวลาที่ใช้พิมพ์ (ถ้าเร็วเกินไปอาจเป็นบอท)
    end_time = time.time()
    duration = end_time - float(start_time)
    
    if user_input.lower() == "apple" and duration > 0.5:
        return f"✅ คุณคือมนุษย์! (ใช้เวลาพิมพ์ {duration:.2f} วินาที)"
    elif duration <= 0.5:
        return f"🚨 ตรวจพบความผิดปกติ! คุณพิมพ์เร็วเกินไป ({duration:.2f} วินาที) น่าจะเป็นบอท!"
    else:
        return "❌ ข้อมูลไม่ถูกต้อง"

with gradio.Blocks() as demo:
    gradio.Markdown("# 🤖 ระบบตรวจจับมนุษย์ (Simple Bot Detector)")
    
    # เก็บเวลาที่หน้าเว็บโหลด
    start_time_state = gradio.State(value=str(time.time()))
    
    user_input = gradio.Textbox(label="พิมพ์คำว่า 'apple' ลงในช่องนี้")
    output = gradio.Textbox(label="ผลลัพธ์")
    
    btn = gradio.Button("ตรวจสอบ")
    btn.click(fn=check_identity, inputs=[user_input, start_time_state], outputs=output)

demo.launch()
