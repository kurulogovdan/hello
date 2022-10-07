"""
    filename goes without an extention
"""
import requests
def donwnload_photo(media_id, filename):
    media = bot.get_media_info(media_id)[0]
    if ("image_versions2" in media.keys()):
        url = media["image_versions2"]["candidates"][0]["url"]
        response = requests.get(url)
        with open(filename + ".jpg", "wb") as f:
            response.raw.decode_content = True
            f.write(response.content)
    elif("carousel_media" in media.keys()):
        for e, element in enumerate(media["carousel_media"]):
            url = element['image_versions2']["candidates"][0]["url"]
            response = requests.get(url)
            with open(filename + str(e) + ".jpg", "wb") as f:
                response.raw.decode_content = True
                f.write(response.content)
                
