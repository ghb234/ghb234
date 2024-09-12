# Hintergrundanimation erstellen
clip = mpy.ColorClip(size=(1080, 1920), color=(255, 255, 255), duration=5)

# Text einfügen
txt_clip = mpy.TextClip("Hello, this is a bouncing ball!", fontsize=70, color='black', font="Amiri-Bold")
txt_clip = txt_clip.set_pos('center').set_duration(5)

# Animation eines Balls (Einfacher Kreis)
ball_clip = mpy.ImageClip(color_gradient((100, 100), p1=(0, 0), p2=(100, 50), col1=(255, 0, 0), col2=(255, 255, 255)))
ball_clip = ball_clip.set_duration(5).set_position(lambda t: (540, 960 + 300 * abs(mpy.np.sin(t))))

# Kombiniere Video und Animationen
final_clip = mpy.CompositeVideoClip([clip, txt_clip, ball_clip])
final_clip.write_videofile("bouncing_ball.mp4", fps=24)


